# 前言

这本书是 UNIX 的“另一本”书。手册没讲的、你的 UNIX 入门书没讲的、你的 UNIX 课程没讲的，它全都讲了。这本书琢磨的是怎么读懂字里行间的意思——而学 UNIX，大体上就是这么回事。

不过，读《UNIX 生活》，你不用费劲去猜字缝里的意思。我们把话全挑明了：别的书字里行间缺的那些，加上 UNIX 的过去、现在和未来，还有我们能想到的其他一切。哦，对了，凡是挖得到的重要轶事和古怪的 UNIX 幽默，我们也全都收了进来。

不管别人怎么告诉你，UNIX 都不是光靠手册、甚至光靠源码就能学会的。UNIX 远不止这些。要理解 UNIX，就得理解它的用户和应用，也得理解它的失败和缺陷。这只是本书希望涵盖的一部分内容。

你得清楚这本书不是什么。它不是一本讲 C 或 UNIX 编程的教科书（这类好书已经够多了）。你不会学到怎么写 shell 脚本，也不会知道内核里有什么。好吧，也许能知道一点点。但你会学到很多有用的东西——正好填上你已经掌握的那些关于 UNIX 的有用和无用的知识之间的缝隙。

我们愿意相信，这本书有点像 Ted Nelson 的《Computer Lib》和《Whole Earth Catalog》的结合体，只不过完全聚焦在 UNIX 上。无论你是 UNIX 新手还是老手，都能从中得到有用的东西。如果你用 VM 在大型机上编程，用 DOS 在微型机上编程，或者用别的什么专有操作系统，你会知道那些厂商一直想瞒着你的是什么。同时，你也会见识到关于 UNIX 的种种鬼话。我们不留情面——UNIX 有长处也有短板，这两面我们都谈。

## 免责声明

这本书是我们两位作者对 UNIX 所知的一次汇总。我们尽力呈现自己所知的真相。有些历史信息格外难查：它们似乎只在 UNIX 大师之间口口相传，除此之外再无严格的记录。

书中提到任何具体的公司、品牌或产品，都不代表作者为它们背书。

## 致谢

感谢 Sol 和 Lennie Libes 通读了多版草稿，检查技术准确性与语法风格。感谢 Susan Libes、Stephen Clark、Dave Fiedler、Larry Welsch、Faye Taxman、Ken Manheimer 和 Janet Shapiro 的校对与宝贵批评。感谢 Tony Shaw 替我们翻遍了专利局的文件。

感谢 Marc Rochkind、Greg Chesson、Rick Rashid、Mel Ferentz、Dick Haight、Mike Accetta、Peter Langston、Ken Arnold、Ted Dolotta、Doug Gwyn、Ed Barkmeyer、Dave Yost、Guy Harris、Chris Torek、Tom Duff、Rob Rosenthal、Donn Seeley 和 George Goble 在挖掘 UNIX 历史的过程中与我们进行了极其愉快而宝贵的交谈。也感谢 UNIX 用户社区——尤其是 Usenet：本书中许多难以找到、此前从未发表过的材料，都是它打捞上来的。

感谢我们那批 UNIX 专家，他们居然有耐心把我们错误百出的草稿读完。找 UNIX 专家本来就不容易，何况还得让他们啃下 350 页、在我们定下的期限内拿出有见地的意见。Brian Kernighan 帮我们审阅了“历史”一章，并和研究部门的人核对了事实。Armando Stettner 向我们介绍了早年贝尔实验室和 DEC 的情况。Mike O’Dell 就全书提出了许多建议。John Quarterman 修正了我们“标准”一节里的许多错误。最后，特别感谢 Eric Allman，他纠正了我们关于伯克利以及 UNIX 世界其他部分的许多失实说法，让这本书比原本可能达到的水平好得多。

我们的 UNIX 专家里，还有 Prentice Hall 提供的匿名审稿人，他们对多版草稿提出了批评意见。此外，David Greenstein 只看过大纲和几章还很粗略的内容，就请 Prentice Hall 鼓励我们把书剩下的部分写完。

最后，感谢 Prentice Hall 的全体员工，是他们专业的工作让这本书看起来如此精美。这里特别要提一下：我们和负责制作的 Sophie Papanikolaou 合作得非常愉快。她同时还在处理另外 20 本书，却让我们看到：哪怕一天 24 小时都在追求完美，也依然可以保持幽默感。感谢她，也感谢所有帮过忙的人。

Don Libes

Sandy Ressler
