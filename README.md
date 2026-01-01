# tg-notify

Simple command line interface to send notifications through Telegram Bot.

## Installation

### Archlinux AUR

```bash
git clone https://aur.archlinux.org/tg-notify.git
cd tg-notify
makepkg -si
```

or using AUR helper

```bash
paru -S tg-notify
# or
yay -S tg-notify
```

### Manual

Ensure dependencies are installed:

- bash
- coreutils
- util-linux
- sed
- curl
- jq

Then, download `tg-notify` shell script and make it executable.

```bash
curl -LO 'https://github.com/liljaylj/tg-notify/releases/latest/download/tg-notify'
chmod +x tg-notify
```

## Usage

### Pre-requisites. Bot API.

In order to be able to send notifications through Telegram Bot (existing or create new with @BotFather), you need to set its API key.

```bash
tg-notify set-token
```

### Add chat

Next, you need to add a chat where notifications will be sent to. You can PM bot or add bot to group and send message there.

```bash
tg-notify add-chat
```

You can add multiple chats to send out notifications.

### Send notifications

To send notifications, you can use the `send` commands.

```bash
tg-notify send hello
```

This command will send a "hello" message to all the chats in list that were added in the previous step.

You can specify which chats notifications will be sent to. To do this, list the chat ID prefixes.

Say we have such list of chats:

```
-1231231234 Test Group 1
-1239878988 Test Group 2
-4328829929 Test Group 3
234234234 liljaylj
```

```bash
tg-notify send '‼️ Backup failed!' @123 234234
```

This will send '‼️ Backup failed!' message to 2 groups: `Test Group 1`, `Test Group 2` and to user `liljaylj`.

### Command usage

```
tg-notify usage:

tg-notify set-token                                           set Bot API token
tg-notify remove-token                                        remove Bot API token
tg-notify add-chat                                            add chat to chat-list
tg-notify list-chats                                          print chat-list
tg-notify remove-chat [chat id]                               remove chat from chat-list
tg-notify [-f|--format <format>] send [msg] [*chat ids]       send message
tg-notify -h|--help|usage|help                                display this help message

Format options:

    2|m|md|markdown       - MarkdownV2
    h|html                - HTML
    1|o|old|markdown1     - Markdown

Note: You can replace "-" prefix in group ID with "@" or enter it after --.
```
