#!/bin/bash

device="${BLOCK_INSTANCE:-wlan0}"
status=$(cat /sys/class/net/${device}/operstate)

URGENT_VALUE=20

if [[ "${status}" == "up" ]]; then
  if [[ -d "/sys/class/net/${device}/wireless" ]]; then
    quality=$(grep ${device} /proc/net/wireless | awk '{ print int($3 * 100 / 70) }')
    echo "${quality}%"
    echo "${quality}%"
    echo ""

    if [[ "${quality}" -le "${URGENT_VALUE}" ]]; then
      exit 33
    fi
  else
    echo "on"
    echo "on"
    echo ""
  fi
fi