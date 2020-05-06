---
title: Externí propojení
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233734"
---
# <a name="external-linkage"></a>Externí propojení

Pokud první deklarace na úrovni oboru souborů pro identifikátor nepoužívá specifikátor třídy úložiště **static** , má objekt vnější propojení.

Pokud deklarace identifikátoru funkce nemá žádný *specifikátor třídy úložiště*, je jeho propojení určeno přesně tak, jako by bylo deklarováno pomocí `extern` *specifikátoru třídy úložiště* . Pokud má deklarace identifikátoru objektu rozsah souboru bez *specifikátoru třídy úložiště*, je jeho propojení externí.

Název identifikátoru s vnějším propojením na stejnou funkci nebo objekt dat provádí ostatní deklarace pro stejný název pomocí vnějšího propojení. Ve stejné jednotce překladu nebo v různých jednotkách překladu mohou být dvě deklarace. Pokud má objekt nebo funkce také globální životnost, jsou funkce nebo objekt sdíleny napříč celým programem.

## <a name="see-also"></a>Viz také

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)
