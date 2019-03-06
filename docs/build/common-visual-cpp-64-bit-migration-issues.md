---
title: Obecné problémy migrace v 64bitovém prostředí Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: c74766c86048f6dd7358d16b8d5d1f2b493450c1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414418"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Obecné problémy migrace v 64bitovém prostředí Visual C++

Pokud použijete Visual C++ k vytvoření aplikace, které poběží v operačním systému Windows 64-bit, byste měli znát následující problémy:

- `int` a `long` jsou 32bitové hodnoty v operačních systémech Windows 64-bit. Pro programy, které máte v plánu pro 64bitové platformy by měl být pozor, abyste jim ukazatele na 32bitové proměnné. Ukazatele jsou 64-bit na 64bitové platformy a zkrátit hodnota ukazatele, pokud přiřadíte 32bitové proměnné.

- `size_t`, `time_t`, a `ptrdiff_t` jsou hodnoty 64bitových operačních systémech Windows 64-bit.

- `time_t` je 32bitová hodnota v operačních systémech Windows 32-bit ve verzích Visual C++ před Visual C++ 2005. `time_t` je teď 64bitovou celočíselnou hodnotu ve výchozím nastavení. Další informace najdete v tématu [Správa času](../c-runtime-library/time-management.md).

   Byste měli vědět, kde váš kód používá `int` hodnotu a zpracovává ji jako `size_t` nebo `time_t` hodnotu. Je možné, že číslo může být větší než 32bitová čísla a data bude zkrácen, pokud je předán zpět do `int` úložiště.

%X (hexadecimální `int` formátu) `printf` modifikátor nebude fungovat podle očekávání v operačním systému Windows 64-bit. Toto pravidlo bude pracovat pouze s prvních 32 bitů hodnotu, která je předána.

- % I32x, chcete-slouží k zobrazení na integrálový typ 32-bit v šestnáctkovém formátu.

- % I64x slouží k zobrazení 64bitového celočíselného typu v šestnáctkovém formátu.

- %P (šestnáctkovém formátu pro ukazatel) bude fungovat podle očekávání v operačním systému Windows 64-bit.

Další informace naleznete v tématu:

- [Možnosti kompilátoru](../build/reference/compiler-options.md)

- [Tipy pro migraci](/windows/desktop/WinProg64/migration-tips)

## <a name="see-also"></a>Viz také:

[Konfigurace Visual C++ pro 64bitové cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
