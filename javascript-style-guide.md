# Powerformer JavaScript Style Guide() {

*A mostly reasonable approach to JavaScript*

## 目录

  1. [代码风格](#code-style)

## 代码风格

  - [1.1](code-style-indent) 语句块内每行代码缩进`4`个空格.

    ```javascript
    // bad
    function heros() {
      if (x) {
        return x;
      } else {
        return y;
      }
    }

    // good
    function heros() {
        if (x) {
            return x;
        } else {
            return y;
        }
    }
    ```
    
  - [1.2](code-style-limit-row) 每行代码不超过`119`个字符.

    ```javascript
    // bad
    const myBadDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis dicta maxime at ratione assumenda, quos, asperiores odit deleniti quia quidem atque quo tempore error a nihil impedit excepturi aliquid nemo?";

    // good
    const myGoodDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. \
                Officiis dicta maxime at ratione assumenda, quos, asperiores odit \
                deleniti quia quidem atque quo tempore error a nihil impedit      \
                excepturi aliquid nemo?";
    ```
};