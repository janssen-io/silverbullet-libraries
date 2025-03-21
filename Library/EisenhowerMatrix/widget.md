---
tags: template
description: Show all things on my TODO list
hooks.bottom:
  where: 'name =~ /^Journal/'
---

# Tasks
## Do
${template.each(eisenhower.query_do(), eisenhower.tpl_task)}
## Plan
${template.each(eisenhower.query_plan(), eisenhower.tpl_task)}
## Delegate
${template.each(eisenhower.query_delegate(), eisenhower.tpl_task)}
## Miscellaneous
${template.each(query[[
  from index.tag "task"
  where not table.includes(tags, "important")
    and not table.includes(tags, "urgent")
    and state != "x"
  order by deadline]], eisenhower.tpl_task)}

---
