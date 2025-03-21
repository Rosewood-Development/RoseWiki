A tokenizer allows detecting an input and converting it to an output.
For example, the [PAPIPlaceholderTokenizer](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/message/tokenizer/placeholder/PAPIPlaceholderTokenizer.java)) uses PlaceholderAPI to convert a placeholder such as `%player_name%` to an output.<br>
Other tokenizers convert things like `&c` to red, or a replacement like `<3` to ❤️.<br>

One example of creating your own tokenizer can be seen in the [HeldItemTokenizer](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/api/example/HeldItemTokenizer.java).<br>

This method in the HeldItemTokenizer is how a tokenizer is registered.
```java
Tokenizers.DEFAULT_BUNDLE.registerBefore(Tokenizers.ROSECHAT_PLACEHOLDER, this);
```
This registers the tokenizer before another tokenizer. This is important as some tokenizers may need priority over other tokenizers.<br>
This tokenizer will be registered into the DEFAULT_BUNDLE, which means all messages using this will use the new tokenizer.<br>

```java
    @Override
    public TokenizerResult tokenize(TokenizerParams params) {
        // This is the string passed to the tokenizer.
        String input = params.getInput();

        // Here you should check if your token is found in the text.
        // If you wanted to change !<Text> to &c&l<Text>, you should check if the message starts with a !.
        if (!input.startsWith("!")) return null;
        
        // A TokenizerResult needs to be returned.
        // Using Token.text() allows plain text to be returned.
        return new TokenizerResult(Token.text("Hello"), input.length());
        
        // Token.group() allows text that can be further tokenized.
        // This will allow &c to turn into red, and &l to turn into bold.
        // Token.group() is a builder and has options that may be useful for you.
        // For example, encapsulate() stops the colour from passing to the next word in the chat message.
        return new TokenizerResult(Token.group("&c&l" + params)
                .encapsulate()
                .build(), input.length());
    }
```

If a tokenizer shouldn't be used in every message, then creating a new `TokenizerBundle` and using `MessageTokenizer.tokenize()` may be useful.
