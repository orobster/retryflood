# retryflood

**识别智能体在短时间内的密集重试。**

`retryflood` —— 按时间窗口统计重试密度，标出触发风暴的失败类型

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`retryflood.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install orobster-retryflood
```

装完直接用命令名调用：

```bash
retryflood --help
```

也可以不用安装，直接把 `retryflood.py` 拷走用——它只依赖标准库。

## 为什么需要它

重试本身合理，问题只在密度上——工具只看密度不看次数

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 智能体重试风暴 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python retryflood.py --file input.txt
python retryflood.py --text "示例内容"
python retryflood.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 时间排序按事件自带时间戳，不做时钟校正。
- 不判断因果，只呈现先后与重叠。

## 跑测试

```bash
python test_retryflood.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/orobster/retryflood>

---

## 关于作者

orobster 做智能体重试风暴相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://orobster.github.io>
- 仓库：<https://github.com/orobster/retryflood>

## 许可

MIT，见 [LICENSE](LICENSE)。
