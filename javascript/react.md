# Powerformer React Style Guide() {

*A mostly reasonable approach to Coding*

> **注意**: 一般的变量命名会以涵盖标题为主，涉及四个值得变量命名会使用`top, right, bottom, left`, 涉及少于四个或者大于四个的变量命名会使用`first, second ...`。

## 目录 <a id="table-of-contents"></a>

  1. [代码风格](#code-style)

## 代码风格 <a id="code-style"></a>

  - [1.1](#code-style-location) 组件中，所有的变量或方法必须得在某一处一致引用,在结尾一致导出。

    ```javascript
    // bad

    render () {
      return (
        <div>
          <p>{this.props.content}</p>
          <button onClick={this.props.handleClick}>first</button>
        </div>
      )
    }

    // good
    render () {
      const { content, handleClick } = this.props;

      return (
        <div>
          <p>{content}</p>
          <button onClick={handleClick}>first</button>
        </div>
      )
    }
    ```

}