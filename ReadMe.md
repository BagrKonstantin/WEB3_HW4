# HW4
## Изменения

До изменений: https://prover.certora.com/output/4932088/7910e73432e64114b0937af74577e9a7?anonymousKey=2b00805ae1d6365bc4638048156b40dfc458b4f5

После изменений: https://prover.certora.com/output/4932088/5632b8a4ab9f4f668de5e5b835152df5?anonymousKey=f48742d4cb60dc2e2ffa796d14f2f7e85e3e9e3e

Были изменены функции transfer и transferFrom.

## Запуск Certora Prover

```bash
certoraRun certora/conf/default.conf --optimistic_loop
```

## Нарушение правил
1. Rules: mint behavior and side effects.
    - Свойство нарушается, так как вместо перевода у получателя печатаются токены на счете
2. Rules: burn behavior and side effects.
   - Свойство нарушается, так как вместо перевода у держателя пропадают токены на счете
3. Rules: only the token holder or an approved third party can reduce an account's balance
   - Свойство нарушается, так как нет проверки на то, есть ли у отправителя разрешение тратить токены
4. Rules: transfer behavior and side effects.
   - Свойство transfer нарушается, так как вместо перевода у получателя печатаются токены на счете, а у отправителя не убавляются
5. Rule: transferFrom behavior and side effects.
   - Свойство transferFrom нарушается, так как вместо перевода у держателя пропадают токены на счете, а у получателя не прибавляются
6. Rules: only mint and burn can change total supply
   - Total supply очень часто меняется))