---
title: Kontrola přepisování paměti použitím ladění sestavení
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314283"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Kontrola přepisování paměti použitím ladění sestavení

Chcete-li použít sestavení ladění pro kontrolu velikosti paměti, je nutné nejprve znovu sestavit projekt pro ladění. Pak pokračujte na začátek `InitInstance` funkce vaší aplikace a přidejte následující řádek:

```
afxMemDF |= checkAlwaysMemDF;
```

Alokátor paměti ladění přináší Guard bajty kolem všech přidělení paměti. Tyto bajty Guard ale nefungují správně, pokud nezjistíte, jestli se změnily (což by znamenalo přepsání paměti). V opačném případě poskytuje pouze vyrovnávací paměť, která může ve skutečnosti mít za následek přepsání paměti.

`checkAlwaysMemDF`Zapnutím nástroje vynutíte, aby knihovna MFC `AfxCheckMemory` vyvolala funkci pokaždé, když je provedeno volání funkce **New** nebo **Delete** . Pokud se zjistilo přepsání paměti, vygeneruje se zpráva trasování, která vypadá podobně jako v následujícím příkladu:

```
Damage Occurred! Block=0x5533
```

Pokud se zobrazí jedna z těchto zpráv, musíte projít kód, abyste zjistili, kde došlo k poškození. Chcete-li přesně izolovat, kde došlo k přepsání paměti, můžete provádět explicitní volání `AfxCheckMemory` sami. Příklad:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Pokud je první kontrolní výraz úspěšný a druhý z nich selže, znamená to, že došlo k přepsání paměti ve funkci mezi dvěma voláními.

V závislosti na povaze vaší aplikace může dojít k tomu, že `afxMemDF` by program běžel příliš pomalu a ještě netestoval. `afxMemDF` Proměnná způsobí `AfxCheckMemory` volání pro každé volání New a DELETE. V takovém případě byste měli v takovém případě zablokovat vlastní volání `AfxCheckMemory`(), jak je znázorněno výše, a pokusit se o izolaci paměti tímto způsobem.

## <a name="see-also"></a>Viz také

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
