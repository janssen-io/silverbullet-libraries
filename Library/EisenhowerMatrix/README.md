# Eisenhower Matrix

The Eisenhower Matrix is a method to prioritize your Todo's.
It uses a quadrant to specify whether you need to do things now, schedule them
for later, delegate them or remove them from your list altogether.

|                   |            |                |
|-------------------|------------|----------------|
| **Important**     | Do Now     | Plan           |
| **Not Important** | Delegate   | Delete         | 
|                   | **Urgent** | **Not Urgent** |

## Usage
Mark your Todo's with the following tags to automatically show at the bottom of
your journal:

- #urgent
- #not-urgent
- #important
- #not-important

## Example:

The following Todo's will be shown as follows:

```markdown
# Journal/Day/2025-02-28

- [ ] Order new desks #urgent #not-important 📅 2025-03-01
- [ ] Send design doc to architect #urgent #important
```

```markdown
# Tasks

## Do
- [ ] () [[2025-02-28]]: Send design doc to architect

## Plan

## Delegate
- [ ] (2025-03-01) [[2025-02-28]]: Order new desks

## Miscellaneous
```

### Data
- [ ] Rewrite commands in Lua #urgent #important
- [ ] Write documentation #important #not-urgent
- [ ] Spread the good word on the forums #not-important #urgent

#### Do
${template.each(eisenhower.query_do(), eisenhower.tpl_task)}
#### Plan
${template.each(eisenhower.query_plan(), eisenhower.tpl_task)}
#### Delegate
${template.each(eisenhower.query_delegate(), eisenhower.tpl_task)}


## Template and functions
```space-lua
eisenhower = eisenhower or {}

eisenhower.tpl_task = template.new [=[
  * [${state}] ${deadline or ""} [[${ref}]]: ${name} 
]=]

eisenhower.query_do = function()
  return query[[
    from index.tag "task"
    where table.includes(tags, "important")
      and table.includes(tags, "urgent")
      and state != "x"
  ]]
end

eisenhower.query_plan = function()
  return query[[
    from index.tag "task"
    where table.includes(tags, "important")
      and not table.includes(tags, "urgent")
      and state != "x"
  ]]
end

eisenhower.query_delegate = function()
  return query[[
    from index.tag "task"
    where not table.includes(tags, "important")
      and table.includes(tags, "urgent")
      and state != "x"
  ]]
end