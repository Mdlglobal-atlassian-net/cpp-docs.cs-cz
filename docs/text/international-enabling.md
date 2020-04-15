---
title: Podpora národních prostředí
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375803"
---
# <a name="international-enabling"></a>Podpora národních prostředí

Většina tradiční kód C a C++ umožňuje předpoklady o charakter a řetězec manipulace, které nefungují dobře pro mezinárodní aplikace. Zatímco knihovna MFC i knihovna za běhu podporují kódování Unicode nebo MBCS, stále je práce, kterou můžete provést. Tato část vysvětluje význam "mezinárodního povolení" ve visual c++:

- Unicode i MBCS jsou povoleny pomocí přenosných datových typů v seznamech parametrů funkce knihovny MFC a návratových typech. Tyto typy jsou podmíněně definovány vhodnými způsoby v `_UNICODE` závislosti na `_MBCS` tom, zda sestavení definuje symbol nebo symbol (což znamená DBCS). Různé varianty knihovny knihovny Knihovny MFC jsou automaticky propojeny s vaší aplikací, v závislosti na tom, které z těchto dvou symbolů sestavení definuje.

- Kód knihovny tříd používá přenosné funkce za běhu a další prostředky k zajištění správného chování Unicode nebo MBCS.

- Stále je nutné zpracovat určité druhy úkolů internacionalizace v kódu:

  - Používejte stejné přenosné funkce za běhu, díky kterým je knihovna MFC přenosná v obou prostředích.

  - Pomocí makra vytvořte přenosné literálové `_T` řetězce a znaky v obou prostředích. Další informace naleznete [v tématu Mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md).

  - Při analýzách řetězců pod mbcs. Tato opatření nejsou potřeba v rámci Unicode. Další informace naleznete [v tématu MBCS Programming Tips](../text/mbcs-programming-tips.md).

  - Dbejte na to, pokud v aplikaci smícháte znaky ANSI (8bit) a Unicode (16 bit). V některých částech programu je možné použít znaky ANSI a znaky Unicode v jiných, ale nelze je kombinovat ve stejném řetězci.

  - Nepoužívejte pevné řetězce kódu v aplikaci. Místo toho je proveďte stringtable prostředky jejich přidáním do souboru .rc aplikace. Aplikace pak může být lokalizována bez nutnosti změny zdrojového kódu nebo rekompilace. Další informace o stringtable prostředky naleznete v [tématu String Editor](../windows/string-editor.md).

> [!NOTE]
> Evropské znakové sady a znakové sady MBCS mají některé znaky, například písmena s diakritikou, s kódy znaků většími než 0x80. Vzhledem k tomu, že většina kódu používá podepsané znaky, jsou tyto znaky větší než 0x80 při převodu na **int**prodlouženy. To je problém pro indexování pole, protože znaménko rozšířené znaky, jsou negativní, indexuje mimo pole. Jazyky, které používají mbcs, jako je například japonština, jsou také jedinečné. Vzhledem k tomu, že znak se může skládat z 1 nebo 2 bajtů, měli byste vždy manipulovat s oběma bajty současně.

## <a name="see-also"></a>Viz také

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Strategie internacionalizace](../text/internationalization-strategies.md)
