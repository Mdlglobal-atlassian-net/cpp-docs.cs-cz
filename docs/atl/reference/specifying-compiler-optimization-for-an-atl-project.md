---
title: Určení optimalizace kompilátoru pro projekt ATL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630616"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Určení optimalizace kompilátoru pro projekt ATL

Ve výchozím nastavení generuje [Průvodce ovládacím prvkem ATL](../../atl/reference/atl-control-wizard.md) nové třídy pomocí makra ATL_NO_VTABLE následujícím způsobem:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL pak definuje _ATL_NO_VTABLE následujícím způsobem:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Pokud nedefinujete _ATL_DISABLE_NO_VTABLE, makro ATL_NO_VTABLE se rozbalí na `declspec(novtable)`. Použití `declspec(novtable)`v deklaraci třídy brání v inicializaci ukazatele vtable v konstruktoru třídy a destruktoru. Při sestavování projektu linker vyloučí vtable a všechny funkce, na které odkazuje tabulka.

Je nutné použít ATL_NO_VTABLE, a v `declspec(novtable)`důsledku toho pouze základní třídy, které nejsou přímo vyčistěné. Nesmíte `declspec(novtable)` použít s nejvíce odvozenou třídou v projektu, protože tato třída (obvykle [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md)nebo [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) inicializuje ukazatel vtable pro váš projekt.

Virtuální funkce nesmí být volána z konstruktoru žádného objektu, který používá `declspec(novtable)`. Měli byste přesunout tato volání do metody [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) .

Pokud si nejste jistí, jestli byste měli `declspec(novtable)` použít modifikátor, můžete odebrat makro ATL_NO_VTABLE z jakékoli definice třídy, nebo ho můžete globálně zakázat zadáním

```
#define _ATL_DISABLE_NO_VTABLE
```

v souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) před tím, než budou zahrnuty všechny ostatní hlavičkové soubory ATL.

## <a name="see-also"></a>Viz také:

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[C++typy projektů v aplikaci Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
