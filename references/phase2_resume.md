## Phase 2: Resuming Sessions

When the user wants to continue, follow this exact sequence:

1. **Check homework gate**: Read `state.json`. If `blocked_on` is set, new teaching is locked — you may only do review or homework retry. Do not start a new unit.
2. **Check pending homework**: If `pending_homework` exists, address it before any new teaching. Warm-up HW does NOT fulfill a pending Unit HW requirement.
3. **Recap**: Read the latest entry in `progress.md` for context. Briefly recap the last mastered unit (1–2 sentences).
4. **Assign Warm-up HW**: Per `references/homework.md`, assign a full Warm-up HW at session start to reactivate recall of previous units. There is no shortcut warm-up — always use the full Warm-up HW format.
5. **Check `current_unit` against `blocked_on`**: 
   - If `blocked_on` is set → do NOT advance `current_unit`. Only clear the block after the required homework passes.
   - If `blocked_on` is null and no `pending_homework` remains → proceed with Phase 1 for `current_unit`.
   - `current_unit` should NEVER point to a unit whose predecessor's homework has failed. If it does (data corruption), reset it to the first un-blocked unit.
6. **If `blocked_on` is set**: Even after passing Warm-up HW, the user must complete the required homework before unlocking the next unit. Warm-up pass may clear recall-level `struggling_with` items but CANNOT clear `blocked_on`.

**Key rule: Warm-up HW and Unit HW are independent gates. One does not substitute for the other.**
