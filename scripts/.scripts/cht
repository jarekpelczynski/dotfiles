#!/usr/bin/env bash

languages=$(echo "golang typescript rust ruby" | tr " " "\n")
core_utils=$(echo "git curl wget find xargs sed awk" | tr " " "\n")

selected=$(echo -e "$languages\n$core_utils" | fzf)


tmux split-window -h bash -c "read -p \"Search: \" query"

if echo $languages | grep -qs $selected; then
	curl cht.sh/$selected/$(echo "$query" | tr " " "+") | less
else
	curl cht.sh/$selected~$query | less
fi
