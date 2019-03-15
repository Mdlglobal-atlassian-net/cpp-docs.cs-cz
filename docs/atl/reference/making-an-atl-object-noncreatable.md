---
title: Vytváření Noncreatable objektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 966c7c1e42cd707726a8ca65bb80914c29ad582e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814498"
---
# <a name="making-an-atl-object-noncreatable"></a>Vytváření Noncreatable objektu ATL

Atributy objektu COM založený na knihovně ATL můžete změnit tak, aby klient nelze přímo vytvořit objekt. V takovém případě objekt by být vráceny prostřednictvím volání metody na jiném objektu spíše než přímo vytvořeny.

## <a name="to-make-an-object-noncreatable"></a>K zamezení vytvoření objektu

1. Odeberte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pro objekt. Pokud chcete, aby objekt, který má být nešel vytvořit, ale ovládací prvek k registraci, nahraďte OBJECT_ENTRY_AUTO s [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Přidat [noncreatable](../../windows/noncreatable.md) atribut coclass v souboru IDL. Příklad:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>Viz také:

[Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektů Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
