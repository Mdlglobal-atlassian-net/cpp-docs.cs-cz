---
title: Externí propojení
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148774"
---
# <a name="external-linkage"></a>Externí propojení

Pokud první deklarace na úrovni rozsahu souboru identifikátoru nepoužívá **statické** specifikátor třídy úložiště, objekt má vnější propojení.

Pokud deklarace identifikátoru funkce nemá žádné *storage-class-specifier*, jeho propojení určeno stejně, jako kdyby byly deklarovány s *storage-class-specifier* `extern`. Pokud má deklarace identifikátoru objektu rozsah souboru a ne *storage-class-specifier*, je její propojení externí.

Název identifikátoru s vnějším propojením na stejnou funkci nebo objekt dat provádí ostatní deklarace pro stejný název pomocí vnějšího propojení. Ve stejné jednotce překladu nebo v různých jednotkách překladu mohou být dvě deklarace. Pokud má objekt nebo funkce také globální životnost, jsou funkce nebo objekt sdíleny napříč celým programem.

## <a name="see-also"></a>Viz také:

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)
