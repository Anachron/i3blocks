#!/bin/bash
# Source: http://www.onlamp.com/pub/a/linux/2000/11/16/LinuxAdmin.html

INSTANCE="${BLOCK_INSTANCE}"
# If you don't like you can use any other IP
INTERFACE="$(ip route get 8.8.8.8 | grep -Po '(?<=(dev )).*(?= src)')"

if [[ "${INSTANCE}" = "" ]]; then
  INSTANCE="${INTERFACE};both"
fi

DISPLAY=$(echo "${INSTANCE}" | awk -F ';' '{print $2}')
INSTANCE=$(echo "${INSTANCE}" | awk -F ';' '{print $1}')

if [[ "${DISPLAY}" = "" ]]; then
  DISPLAY="both"
fi

ONE_KB=1024
ONE_MB=$(echo "${ONE_KB}*1024" | bc -l)
TEN_MB=$(echo "${ONE_MB}*10" | bc -l)
OHD_MB=$(echo "${TEN_MB}*10" | bc -l)

URGENT_VALUE="${ONE_MB}"

PREV_IN=0
PREV_OUT=0

PREV_FILE="/tmp/.bandwidth"

if [[ -f "${PREV_FILE}" ]]; then
  PREV_CONT=$(cat "${PREV_FILE}")
  PREV_IN=$(echo "${PREV_CONT}" | head -n 1)
  PREV_OUT=$(echo "${PREV_CONT}" | tail -n 1)
fi

BANDWIDTH=$(grep "${INSTANCE}" /proc/net/dev | awk -F: '{print  $2}' | awk '{print $1" "$9}')

if [[ "${BANDWIDTH}" = "" ]]; then
  exit
fi

BYTES_IN=$(echo "${BANDWIDTH}" | awk -F ' ' '{print $1}')
BYTES_OUT=$(echo "${BANDWIDTH}" | awk -F ' ' '{print $2}')

function FormatNumber() {
  if [[ "${1}" -ge "${OHD_MB}" ]]; then
    echo $(echo "scale=0;${1}/${ONE_MB}" | bc -l)"mb"
  elif [[ "${1}" -ge "${TEN_MB}" ]]; then
    echo $(echo "scale=1;${1}/${ONE_MB}" | bc -l)"mb"
  elif [[ "${1}" -ge "${ONE_MB}" ]]; then
    echo $(echo "scale=2;${1}/${ONE_MB}" | bc -l)"mb"
  elif [[ "${1}" -ge "${ONE_KB}" ]]; then
    echo $(echo "scale=0;${1}/${ONE_KB}" | bc -l)"kb"
  else
    echo "${1}""b"
  fi
}

if [[ "${PREV_IN}" != "" ]] && [[ "${PREV_OUT}" != "" ]]; then
  # Calculate the CPU usage since we last checked.
  DIFF_IN=$(echo "scale=0;${BYTES_IN} - ${PREV_IN}" | bc -l)
  DIFF_OUT=$(echo "scale=0;${BYTES_OUT} - ${PREV_OUT}" | bc -l)
  DIFF_TOTAL=0

  USAGE_IN=$(FormatNumber "${DIFF_IN}")
  USAGE_OUT=$(FormatNumber "${DIFF_OUT}")

  if [[ "${DISPLAY}" = "both" ]]; then
    echo "${USAGE_IN} : ${USAGE_OUT}"
    echo "${USAGE_IN} : ${USAGE_OUT}"
    echo ""
    DIFF_TOTAL=$((DIFF_TOTAL+DIFF_IN))
    DIFF_TOTAL=$((DIFF_TOTAL+DIFF_OUT))
  elif [[ "${DISPLAY}" = "in" ]]; then
    echo "${USAGE_IN}"
    echo "${USAGE_IN}"
    echo ""
    DIFF_TOTAL=$((DIFF_TOTAL+DIFF_IN))
  elif [[ "${DISPLAY}" = "out" ]]; then
    echo "${USAGE_OUT}"
    echo "${USAGE_OUT}"
    echo ""
    DIFF_TOTAL=$((DIFF_TOTAL+DIFF_OUT))
  fi
else
  echo "?"
  echo "?"
  echo ""
fi

# Remember the total and idle CPU times for the next check.
echo "${BYTES_IN}" > "${PREV_FILE}"
echo "${BYTES_OUT}" >> "${PREV_FILE}"

if [[ "${DIFF_TOTAL}" -ge "${URGENT_VALUE}" ]]; then
  exit 33
fi
