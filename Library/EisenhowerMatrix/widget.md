---
tags: template
description: Show all things on my TODO list
hooks.bottom:
  where: 'name =~ /^Journal/'
---

# Tasks
## Do
```query
task
where "important" in tags
  and "urgent" in tags
  and state != "x"
render [[Library/EisenhowerMatrix/task-deadline-view]]
```
## Plan
```query
task
where "important" in tags
  and "not-urgent" in tags
  and state != "x"
order by deadline asc
render [[Library/EisenhowerMatrix/task-deadline-view]]
```
## Delegate
```query
task
where "not-important" in tags
  and "urgent" in tags
  and state != "x"
render [[Library/EisenhowerMatrix/task-deadline-view]]
```
## Miscellaneous
```query
task
where tags = []
  and state != "x"
order by deadline asc
render [[Library/EisenhowerMatrix/task-deadline-view]]
```
---