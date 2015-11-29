#!/bin/bash

SSID_NAME=$(iwgetid -r)

# You can put any urgent name so the block will give warning
# if a network with this name is used, like public wifi or alike.
# You can separate multiple values with \|
URGENT_VALUE=""

if [[ "${SSID_NAME}" != "" ]]; then
  echo "${SSID_NAME}"
  echo "${SSID_NAME}"
  echo ""

  if [[ "${URGENT_VALUE}" != "" ]] && [[ $(echo "${SSID_NAME}" | grep -we "${URGENT_VALUE}") != "" ]]; then
    exit 33
  fi
fi