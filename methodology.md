# 方法学

- 深刻理解业务需求 （需求为本）
- 合适地实现需求 （平衡成本和可扩展性）
- tdd（质量保证）
- 有必要立即重构 (增加适应性)

# 开发中的取舍 （排名分先后）
- 交付价值
- 去除重复
- 表达意图

# 敏捷宣言

```
个体互动 高于 流程工具
可工作软件 高于 详尽文档
客户合作 高于 合同谈判
响应变化 高于 遵循计划
右项有其价值，更重视左项
```

# 站会是什么（standup）
- 分享总体进度：每天15分钟的短时间会议
    - what was done?
	- what to be done?
	- blocker?

# 看板（kanban）
- backlog
- ready for dev
- dev ongoing: 开卡前先找BA确认
- dev done
- test ready：test前先做deck check
- testing
- ready for showcase
- done


# 极限编程工程实践

```
	Core
		Test driven design
		Refactoring
		Pair programming
		Simple Design
	2nd Core
		continous integration
		collective ownership: pair and code review
		coding standard
		sustainable pace
		metaphor
	3rd Core
		whole team
		planning Game
		small release
		customer tests

```

# Scrum 中的角色

```
product owner: 资方或BA
    决定哪些功能进、哪些功能不进、优先级是什么
scrum master: team lead
    教练的角色，教会团队自组织、教育PO、教育开发团队、教育组织里其它Stakeholder。评价教练的唯一标准就是被教授的人不再需要他/她了
team member: everyone else, 5-9 people (full functional team)
stages:
    planning: refine product backlog
    daily scrum: sprint backlog (backlog for the current iteration)
    review: demo the product
    retro
```

# Scrum 中的四个会议

```

showcase会议: 获得用户反馈，并对product backlog做出调整
Sprint计划会议：
    IPM(what): iteration planning meeting
         PO应该根据stakholder的输入, 从业务优先级上选出下个sprint的backlog
    IKM(how): iteration kickoff meeting
        PO和开发团队对这个Sprint的目标进行交互解释, 答疑, 达成共识
站会: 
    站会是向整个团队报告进度, 目的是寻求帮助, 提供新知, 为可能的任务调整提供真实的输入
    关注接力棒, 而不是运动员

Sprint回顾会议

```
