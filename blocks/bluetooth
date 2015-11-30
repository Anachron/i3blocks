#!/bin/bash

# Left click
if [[ "${BLOCK_BUTTON}" -eq 1 ]]; then
  sudo bluetooth on
# Middle click
elif [[ "${BLOCK_BUTTON}" -eq 2 ]]; then
  sudo bluetooth toggle
# Right click
elif [[ "${BLOCK_BUTTON}" -eq 3 ]]; then
  sudo bluetooth off
fi

STATUS=$(bluetooth | grep -wo 'on')

if [[ "${STATUS}" = "on" ]]; then
  echo "on"
  echo "on"
  echo ""
fi