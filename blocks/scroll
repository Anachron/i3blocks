#!/bin/bash
# IMPORTANT: 
# To make this block work, you have to edit your block-command.
# It should point to this file. For best performance, only use it on blocks
# which are wide and that you need to scroll.
# 
# Example:
# command=~/.i3-blocks/blocks/scroll $BLOCK_NAME
# markup=pango
# interval=repeat

PROG="${1}"

SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
BLOCK_PATH="${SCRIPT_DIR}/${PROG}"

INTERVAL=0.17
MAX_LENGTH=25
ADD_STR=" | "
ADD_LENGTH=${#ADD_STR}

if [[ -f "${BLOCK_PATH}" ]]; then
  BLOCK_OUT=$(bash "${BLOCK_PATH}")
  OUT_TEXT=$(echo "${BLOCK_OUT}" | tail -n 1)
elif [[ "${PROG}" != "" ]]; then
  OUT_TEXT=$(${PROG})
  if [[ $? -ne 0 ]]; then
    sleep 1
    echo "${PROG}"
    echo "${PROG}"
    exit 33
  fi
fi

if [[ "${OUT_TEXT}" ]]; then
  CHECK_SUM=$(echo "${PROG}-${BLOCK_INSTANCE}" | md5sum | awk '{print $1}')

  TMP_FILE="/tmp/.scroll-${CHECK_SUM}"

  if [[ -f "${TMP_FILE}" ]]; then
    SCROLL_POS=$(cat "${TMP_FILE}")
  else
    SCROLL_POS=0
  fi

  TEXT_LENGTH=${#OUT_TEXT}
  MAX_OFFSET=$((TEXT_LENGTH +ADD_LENGTH -1))

  if [[ "${TEXT_LENGTH}" -lt "${MAX_LENGTH}" ]]; then
    MAX_LENGTH="${TEXT_LENGTH}"
  fi

  if [[ "${SCROLL_POS}" -gt "${MAX_OFFSET}" ]]; then
    SCROLL_POS=0
  fi

  TEXT_LINE="${OUT_TEXT}${ADD_STR}${OUT_TEXT}${ADD_STR}${OUT_TEXT}"
  TEXT_LINE=${TEXT_LINE:$SCROLL_POS:$MAX_LENGTH}

  echo "<span font_family='monospace'>${TEXT_LINE}</span>"
  echo "<span font_family='monospace'>${TEXT_LINE}</span>"

  SCROLL_POS=$((SCROLL_POS +1))

  echo "${SCROLL_POS}" > "${TMP_FILE}"
  sleep "${INTERVAL}"
else
  sleep 1
fi
