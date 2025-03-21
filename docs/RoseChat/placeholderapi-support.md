## Introduction
There are many different uses for PlaceholderAPI in RoseChat. The first is using the custom placeholders that RoseChat provides, which can be found below. Another is the ability to use any placeholder in any message in RoseChat. These messages can be edited in your locale file. Placeholders can also be used in chat, if the player has permission, and in any format defined in placeholders.yml.

## Placeholders

| Placeholder                            | Description                                                                    |
| -                                      | -                                                                              |
| %rosechat_chat_color%                  | The current chat color that the player is using (e.g. &c) .                    |
| %rosechat_name%                        | The player's effective name. The nickname if set, or display name, then falls back to the username if neither could be found.             |
| %rosechat_name_stripped%                        | The player's effective name, without color. |
| %rosechat_nickname%                    | The nickname that the player has, unformatted (e.g. <r:0.3>Lilac).             |
| %rosechat_nickname_stripped%                    | The nickname that the player has, without color.            |
| %rosechat_current_channel%             | The current channel that the player is in.                                     |
| %rosechat_is_muted%                    | Whether or not the player is muted.                                            |
| %rosechat_mute_time%                   | The amount of time left in a player's mute, in seconds.                        |
| %rosechat_has_emojis%                  | Whether or not the player has emojis enabled.                                  |
| %rosechat_has_message_sounds%          | Whether or not the player has message sounds enabled.                          |
| %rosechat_has_tag_sounds%              | Whether or not the player has tag sounds enabled.                              |
| %rosechat_can_be_messaged%             | Whether or not the player has messages enabled.                                |
| %rosechat_has_group_spy%               | Whether or not the player has group spying enabled.                            |
| %rosechat_has_channel_spy%             | Whether or not the player has channel spying enabled.                          |
| %rosechat_has_message_spy%             | Whether or not the player has message spying enabled.                          |
| %rosechat_last_messaged%               | The name of the player that this player last sent a message to.                |
| %rosechat_is_group_leader%             | Whether or not this player is the leader of a group chat.                      |
| %rosechat_group%                       | The name of the group that this player owns.                                   |
| %rosechat_group_<group\>_owner%        | The owner of the given group chat.                                             |
| %rosechat_group_<group\>_name%         | The name of the given group chat, unformatted.                                 |
| %rosechat_placeholder_<placeholder\>%  | The value of the given placeholder, parsed with the given player, unformatted. |
| %rosechat_last_message_<channel\>%     | The last message sent in a channel that has slowmode enabled.<br/>This can be used with or without a player. Using this placeholder will remove the message from the slowmode queue. |
