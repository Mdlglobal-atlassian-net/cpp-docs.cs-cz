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
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321744"
---
# <a name="reference-counting"></a>Počítání odkazů

Com sám se automaticky nepokouší odebrat objekt z paměti, když si myslí, že objekt již není používán. Místo toho musí programátor objektu odebrat nepoužitý objekt. Programátor určuje, zda lze objekt odebrat na základě počtu odkazů.

Com používá `IUnknown` metody [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)ke správě počtu odkazů rozhraní na objektu. Obecná pravidla pro volání těchto metod jsou:

- Vždy, když klient obdrží `AddRef` ukazatel rozhraní, musí být volána na rozhraní.

- Vždy, když klient dokončil pomocí ukazatele rozhraní, musí volat `Release`.

V jednoduché implementaci `AddRef` každé volání přírůstky `Release` a každé volání sníží proměnnou čítače uvnitř objektu. Když se počet vrátí na nulu, rozhraní již nemá žádné uživatele a je volně odebrat sám z paměti.

Počítání odkazů lze také implementovat tak, aby se počítal každý odkaz na objekt (nikoli na jednotlivé rozhraní). V tomto případě `AddRef` `Release` každý a volání delegátů centrální implementace `Release` na objekt a uvolní celý objekt, když jeho počet odkazů dosáhne nuly.

> [!NOTE]
> `CComObject`Při -odvozený objekt je vytvořen pomocí **nového** operátoru, počet odkazů je 0. Proto musí `AddRef` být provedeno volání po úspěšném `CComObject`vytvoření -derived objektu.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Správa životnosti objektů prostřednictvím počítání odkazů](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
