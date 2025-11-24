# 🎉 GlutenCon 2025 首届大会正式启动！

欢迎来到 Apache Gluten 社区的年度盛会 —— **GlutenCon 2025**！
<div align="center">
  <img width="400"  alt="image" src="/assets/images/glutenCon2025.jpg"/>
</div>

📅 日期：2025 年 12 月 6 日（星期六）  
🕘 时间：09:00 - 18:00  
📍 地点：北京 · 字节跳动总部（北京市海淀区北三环西路甲18号院大钟寺广场1号楼）  
🎯 主办方：Apache Gluten 社区 & 字节跳动  

---

## 🧭 活动简介

Apache Gluten 是一个面向数据处理加速的开源项目，致力于通过原生向量化执行、后端解耦架构和现代硬件优化，提升 Spark 等计算引擎的性能表现。

本次大会将汇聚来自社区、企业和学术界的技术专家，围绕 **Apache Gluten 项目进展、执行优化实践、多后端集成、开源治理** 等话题展开深入交流。

---

## 🌟 大会亮点

- **Apache Gluten 项目进展**
- **字节跳动现场发布重要消息**
- **技术分享 + 社区交流 + 实战案例**  
- **午餐、咖啡、纪念品全包**（免费票）

## 📝 报名

🎟 **免费票**：包含午餐、茶歇、纪念品  
📣 **报名方式**：https://bytedance.us.larkoffice.com/share/base/form/shrusjMDU22LxnSXOYwT757eAxc

📣 **加入社群**：请扫描二维码加入群聊以便交流和接受最新资讯

<img width="300" height="303" alt="image" src="/assets/images/1127.png" />

---

## 🗣 演讲嘉宾

- 敬请期待！

---

## 📚 议题安排

- 详情敬请期待！
  
<table>
  <thead>
    <tr>
      <th width="140">时间</th>
      <th width="900">内容</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>08:00 - 9:20</td>
      <td>签到</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>9:20 - 9:30</td>
      <td>欢迎辞</td>
    </tr>
    <tr>
      <td></td>
      <td>
        <details>
          <summary><strong>杨宾伟</strong> IBM <strong>陈伟霆</strong> MSFT</summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>9:30 - 10:00</td>
      <td>keynote：<b> Bolt: 面向多引擎的生产级异构加速库</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>Frank Hu 字节跳动</strong></summary>
          字节跳动引擎加速团队负责人
          <br>
          <br>
        </details>
      </td>
    </tr>
    <tr>
      <td>10:00 - 10:20</td>
      <td>keynote：<b>Apache Gluten 在IBM的现状和发展</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>Ethan Zhang IBM</strong></summary>
          介绍Apache Gluten在IBM团队一年以来的进展，目前的工作，2026年的规划以及长久发展规划
        </details>
      </td>
    </tr>
    <tr>
      <td>10:30 - 11:00</td>
      <td><b>Apache Gluten现在和未来</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>陈伟霆 MSFT</strong></summary>
          <img width="150"  alt="image" src="/assets/images/GlutenCon2025/Weiting.png"/><br>
          微软首席软件工程经理，Apache Gluten PMC 成员，长期积极参与开源社区并协助客户落地 Gluten 解决方案，推动高性能数据处理与技术创新，致力于帮助工程团队与社区共同成长。
          <br>
          <br>
          Apache Gluten 是一个专注于提升 Spark SQL 在多种计算引擎上性能的开源社区项目，旨在通过原生集成与优化，让大规模数据处理更快、更高效。本次分享将带来 Gluten 社区的最新现状，包括项目运营策略、目前已支持的功能，以及未来的技术路线图。我们将深入探讨近期的关键进展、面临的挑战与解决方案，让参与者能够全面了解 Gluten 的发展方向，并思考如何在自己的工作场景中加以应用。
        </details>
      </td>
    </tr>
    <tr>
      <td>11:00 - 11:30</td>
      <td><b>Apache Gluten在字节跳动的落地实践</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>王广新 字节跳动</strong></summary>
          字节
        </details>
      </td>
    </tr>
    <tr>
      <td>11:30 - 12:00</td>
      <td><b>GPU加速在Gluten中的应用</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>靳成成 IBM</strong></summary>
          IBM高级软件研发工程师，Gluten PPMC, Velox maintainer, focus on shuffle, GPU optimization，datalake iceberg native implementation.
          <br>
          <br>
          Gluten + Velox GPU优化， 在Velox中实现其算子，调用rapids libcudf API，cudf封装了CUDA。根据plan特征和代价判断其是否调度到GPU, 在用户实际场景，table scan往往取决于远程存储的吞吐量，难以获得较大的性能提升，而第二个计算密集型的stage可以取得极大的性能提升，在速度和成本上均有优势，以TPCDS Q95 SF100为例，相比cpu native执行，第2个stage将时间从70s降低到13s，提升了5倍。本次分享将详细讲述当前进度，实现方案和未来蓝图。
        </details>
      </td>
    </tr>
    <tr>
      <td>12:00 - 1:00</td>
      <td><b>午饭</b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
      </td>
    </tr>
    <tr>
      <td>1:00 - 1:30</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>1:30 - 2:00</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>2:00 - 2:30</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>2:30 - 3:00</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>3:00 - 3:30</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>3:30 - 4:00</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>4:00 - 4:30</td>
      <td><b>keynote：</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
        <details>
          <summary><strong>杨宾伟 IBM 陈伟霆 MSFT</strong></summary>
          欢迎词
        </details>
      </td>
    </tr>
    <tr>
      <td>4:30 - 5:00</td>
      <td><b>结束/致谢</b></b></td>
    </tr>
    <tr>
      <td> </td>
      <td>
      </td>
    </tr>
  </tbody>
</table>
---

## 🙌 加入我们

无论你是开发者、架构师、数据平台工程师，还是开源爱好者，GlutenCon 都欢迎你的参与！

让我们一起打造一个 **开放、专业、有温度** 的技术盛会！

---

📌 关注 [Apache Gluten GitHub](https://github.com/apache/incubator-gluten) 获取最新动态  
📧 有任何问题欢迎联系：dev@gluten.apache.org
