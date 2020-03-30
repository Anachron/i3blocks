#!/bin/bash
# you will have to enable passwordless sudo ind sudoers file if you want to use this
# Left click
if [[ "${BLOCK_BUTTON}" -eq 1 ]]; then
  sudo ufw enable
# Middle click
elif [[ "${BLOCK_BUTTON}" -eq 2 ]]; then
  sudo ufw reload
# Right click
elif [[ "${BLOCK_BUTTON}" -eq 3 ]]; then
  sudo ufw disable
fi

# to get the status without the dirty sudoers file hack, do this:
#status=$(pgrep -f "ufw" 2>/dev/null)
# else keep this
status=$(sudo ufw status 2>/dev/null)

if [[ $? -gt 0 ]]; then
  exit
fi

if [[ "${status}" != *inactive* ]]; then
  echo "on"
  echo "on"
  echo ""
else
  echo "off"
  echo "off"
  echo ""
fi

