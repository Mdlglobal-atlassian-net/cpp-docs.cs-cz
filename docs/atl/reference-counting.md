---
title: Počítání odkazů (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 565b74956280d4e80c41376ead4249e69980a80e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492224"
---
# <a name="reference-counting"></a>Počítání odkazů

Samotný model COM se automaticky nepokouší odebrat objekt z paměti, když se domnívá, že objekt již není používán. Místo toho musí programátor objektů odebrat nepoužitý objekt. Programátor Určuje, zda lze objekt odebrat na základě počtu odkazů.

Model COM používá `IUnknown` metody, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)pro správu počtu odkazů rozhraní objektu. Obecná pravidla pro volání těchto metod jsou:

- Vždy, když klient obdrží ukazatel rozhraní, `AddRef` musí být volán na rozhraní.

- Pokaždé, když klient dokončí používání ukazatele rozhraní, musí volat `Release`.

V jednoduché implementaci každý `AddRef` přírůstek volání a každé `Release` volání snižuje proměnnou čítače uvnitř objektu. Pokud se počet vrátí na nulu, rozhraní už nemá žádné uživatele a může se z paměti odebrat sám.

Lze také implementovat počítání odkazů tak, aby se každý odkaz na objekt (ne na jednotlivé rozhraní) započítávají. V tomto případě každý z `AddRef` nich `Release` volá delegáty k centrální implementaci objektu a `Release` uvolní celý objekt, pokud jeho počet odkazů dosáhne nuly.

> [!NOTE]
>  Když je objekt odvozený od konstrukce pomocí operátoru new, počet odkazů je 0. `CComObject` Proto `AddRef` musí být volání provedeno po úspěšném vytvoření objektu odvozeného `CComObject`od.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
