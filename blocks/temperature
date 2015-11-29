#!/bin/bash

TEMP_DEVICE="${BLOCK_INSTANCE:-Core}"
TEMP_OUTPUT=$(sensors | grep "${TEMP_DEVICE}")

IS_URGENT=0

TOTAL_TEMP=0
TOTAL_COUNT=0
while read RESULT_LINE; do
  TOTAL_COUNT=$((TOTAL_COUNT +1))
  CURRENT_TEMP=$(echo "${RESULT_LINE}" | grep -o -E "[\+\-]?[0-9]*.[0-9]*°C" | sed -n '1p' | tr -d '+°C')
  URGENT_VALUE=$(echo "${RESULT_LINE}" | grep -o -E "[\+\-]?[0-9]*.[0-9]*°C" | sed -n '2p' | tr -d '+°C')

  TOTAL_TEMP=$(echo "scale=2;${TOTAL_TEMP}+${CURRENT_TEMP}" | bc -l)
  IS_CRITICAL=$(echo "scale=0;${CURRENT_TEMP}-${URGENT_VALUE} >= 0" | bc -l)

  if [[ "${IS_CRITICAL}" -eq 1 ]]; then
    IS_URGENT=1
  fi
done <<< "$(echo -e "$TEMP_OUTPUT")"

AVERAGE_TEMP=$(echo "scale=0;${TOTAL_TEMP}/${TOTAL_COUNT}" | bc -l)

if [[ "${TOTAL_COUNT}" -gt 1 ]]; then
  AVERAGE_TEMP="~ ${AVERAGE_TEMP}"
fi

echo "${AVERAGE_TEMP}°C"
echo "${AVERAGE_TEMP}°C"
echo ""

if [[ "${IS_URGENT}" -eq 1 ]]; then
  exit 33
fi