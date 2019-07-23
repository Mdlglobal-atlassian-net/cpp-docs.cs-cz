---
title: ATL – referenční dokumentace ke kódování
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: a9c7689e49efce0d65e945f1a032a680e2277594
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375862"
---
# <a name="atl-encoding-reference"></a>ATL – referenční dokumentace ke kódování

Kódování v řadě běžných standardů sítě Internet, jako je kódování uuencode, šestnáctková a UTF8, je podporováno kódem nalezeným v atlenc. h.

### <a name="functions"></a>Funkce

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|Dekóduje řetězec dat, který byl kódován jako šestnáctkový text, například předchozí volání [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8.|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|Voláním této funkce převedete data pomocí kódování B.|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|Voláním této funkce převedete znaky, které jsou problematické pro použití v kódu XML, na jejich bezpečné ekvivalenty.|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|Voláním této funkce získáte počet znaků s diakritikou v řetězci.|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|Voláním této funkce zjistíte, zda je daný znak rozšířený znak (menší než 32, větší než 126, a ne karta, posun řádku nebo návrat vozíku).|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|Voláním této funkce převedete data pomocí kódování Q.|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|Dekóduje řetězec dat, která byla zakódována v formátu v uvozovkách, například předchozí volání [QPEncode](reference/atl-text-encoding-functions.md#qpencode).|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.|
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|Voláním této funkce zakódujete data do formátu quoted-printable.|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|Dekóduje řetězec dat, který byl uuencode jako předchozí volání do [kódování uuencode](reference/atl-text-encoding-functions.md#uuencode).|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.|
|[Kódování](reference/atl-text-encoding-functions.md#uuencode)|Voláním této funkce zakódujete data do kódování UUENCODE.|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)
