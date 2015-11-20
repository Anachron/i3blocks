#!/bin/bash

TYPE="${BLOCK_INSTANCE:-caps}"

lockLine=$(xset -q | grep "Num Lock")

capsLock=$(echo "${lockLine}" | awk -F ' ' '{print $4}')
numLock=$(echo "${lockLine}" | awk -F ' ' '{print $8}')
scrollLock=$(echo "${lockLine}" | awk -F ' ' '{print $12}')

if [[ "${TYPE}" == "caps" ]]; then
  checkLock="${capsLock}"
elif [[ "${TYPE}" == "num" ]]; then
  checkLock="${numLock}"
elif [[ "${TYPE}" == "scroll" ]]; then
  checkLock="${scrollLock}"
else
  exit
fi

if [[ "${checkLock}" == "on" ]]; then
  echo "on"
  echo "on"
  echo ""
fi