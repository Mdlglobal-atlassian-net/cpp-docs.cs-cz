---
title: Zadání optimalizace kompilátoru pro projekt knihovny ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: 5b6620b73713886301e4efc29754cf407d9576f4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812340"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Zadání optimalizace kompilátoru pro projekt knihovny ATL

Ve výchozím nastavení [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md) generuje nové třídy s makro ATL_NO_VTABLE následujícím způsobem:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL – potom definuje _ATL_NO_VTABLE následujícím způsobem:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Pokud nedefinujete _ATL_DISABLE_NO_VTABLE, ATL_NO_VTABLE makro rozšíří do `declspec(novtable)`. Pomocí `declspec(novtable)`ve třídě deklarace zabraňuje ukazatel vtable během inicializace v konstruktoru třídy a destruktor. Při sestavování projektu linkeru eliminuje tabulku vtable a všechny funkce, na které odkazuje tabulku vtable.

Je nutné použít ATL_NO_VTABLE a proto `declspec(novtable)`, pouze základní třídy, které nejsou vytvořitelné přímo. Nesmí používat `declspec(novtable)` s nejvíce odvozenému třídu ve vašem projektu, protože tato třída (obvykle [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), nebo [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Inicializuje ukazatel vtable pro váš projekt.

Virtuální funkce nesmějí volat z konstruktoru objektu, který používá `declspec(novtable)`. Měli byste přejít těchto volání [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) metody.

Pokud si nejste jisti, zda byste měli použít `declspec(novtable)` modifikátor, makro ATL_NO_VTABLE můžete odebrat z jakékoli definice třídy, nebo ho globálně zakázat zadáním

```
#define _ATL_DISABLE_NO_VTABLE
```

Ve stdafx.h před všechny ostatní knihovny ATL hlavičkové soubory jsou zahrnuty.

## <a name="see-also"></a>Viz také:

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektů Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
