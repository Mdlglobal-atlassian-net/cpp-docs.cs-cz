---
title: Kontrola přepisování paměti použitím ladění sestavení
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823096"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Kontrola přepisování paměti použitím ladění sestavení

Kontrola přepisování paměti pomocí sestavení pro ladění, je nutné nejprve znovu sestavit projekt pro ladění. Potom přejděte na začátek aplikace `InitInstance` fungovat a přidejte následující řádek:

```
afxMemDF |= checkAlwaysMemDF;
```

Přidělení paměti ladění vloží guard bajtů kolem všechna přidělení paměti. Ale tyto ochrany bajtů neprovádějte žádné funkční, není-li zkontrolovat, zda nebyly změněny (což by označoval přepisování paměti). V opačném případě získáte jenom vyrovnávací paměť, která ve skutečnosti může být, bylo možné okamžitě začít s přepisování paměti.

Zapnutím `checkAlwaysMemDF`, vynutí knihovny MFC pro volání `AfxCheckMemory` pokaždé, když se funkce volání **nové** nebo **odstranit** tvoří. Přepisování paměti byl zjištěn, vygeneruje se zpráva trasování, který bude vypadat nějak takto:

```
Damage Occurred! Block=0x5533
```

Pokud se zobrazí jedna z následujících zpráv, budete muset projít kódu k určení, kde došlo k poškození. Izolace, přesněji kde přepisování paměti došlo k chybě, můžete nastavit explicitního volání `AfxCheckMemory` sami. Příklad:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Pokud první vyhodnocení úspěšné a druhý se nezdaří, znamená to, že přepisování paměti musí mít došlo k chybě ve funkci mezi dvěma voláními.

V závislosti na povaze vašich aplikací, můžete zjistit, která `afxMemDF` způsobí, že váš program pro spuštění příliš pomalu i testování. `afxMemDF` Způsobí, že proměnná `AfxCheckMemory` nelze volat pro každé volání na nový a odstraňovat. V takovém případě by měl bodový vlastní volání `AfxCheckMemory`(jak je uvedeno výše) a zkuste k izolaci paměť přepsat tímto způsobem.

## <a name="see-also"></a>Viz také:

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)