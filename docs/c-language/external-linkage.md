---
title: Externí propojení
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 87e9e16eb115df8d100450f7f0dc44961886ab20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466258"
---
# <a name="external-linkage"></a>Externí propojení

Pokud první deklarace na úrovni rozsahu souboru identifikátoru nepoužívá **statické** specifikátor třídy úložiště, objekt má vnější propojení.

Pokud deklarace identifikátoru funkce nemá žádné *storage-class-specifier*, jeho propojení určeno stejně, jako kdyby byly deklarovány s *storage-class-specifier* `extern`. Pokud má deklarace identifikátoru objektu rozsah souboru a ne *storage-class-specifier*, je její propojení externí.

Název identifikátoru s vnějším propojením na stejnou funkci nebo objekt dat provádí ostatní deklarace pro stejný název pomocí vnějšího propojení. Ve stejné jednotce překladu nebo v různých jednotkách překladu mohou být dvě deklarace. Pokud má objekt nebo funkce také globální životnost, jsou funkce nebo objekt sdíleny napříč celým programem.

## <a name="see-also"></a>Viz také

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)