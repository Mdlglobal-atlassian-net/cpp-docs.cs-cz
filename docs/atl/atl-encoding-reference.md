---
title: "ATL – referenční dokumentace ke kódování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b2a97809fefdc0a5e6e7d90e7b62bbee83f28bfb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-encoding-reference"></a>ATL – referenční dokumentace ke kódování
Kódování v řadu běžných Internetové standardy, jako je uuencode šestnáctkové a UTF8 podporuje kód v atlenc.h nalezen.  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|  
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|Dekóduje řetězec dat, který byl zakódován jako hexadecimální text, například voláním předchozí [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode).|  
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.|  
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.|  
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|  
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8.|  
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|Voláním této funkce převedete data pomocí kódování B.|  
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|  
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|Voláním této funkce převedete znaky, které jsou problematické pro použití v kódu XML, na jejich bezpečné ekvivalenty.|  
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|Voláním této funkce získáte počet znaků s diakritikou v řetězci.|  
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|Voláním této funkce zjistíte, zda daný znak používá diakritiku (je menší než 32, větší než 126 a nejde o tabulátor, odřádkování ani návrat na začátek řádku).|  
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|Voláním této funkce převedete data pomocí kódování Q.|  
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|  
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|Dekóduje řetězec dat, která zakódování ve formátu tisknutelná v uvozovkách, jako předchozí voláním [QPEncode](reference/atl-text-encoding-functions.md#qpencode).|  
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.|  
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|Voláním této funkce zakódujete data do formátu quoted-printable.|  
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|  
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|Dekóduje řetězec dat, která byla uuencoded například voláním předchozí [UUEncode](reference/atl-text-encoding-functions.md#uuencode).|  
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.|  
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|Voláním této funkce zakódujete data do kódování UUENCODE.|  
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [Desktopové komponenty ATL objektů COM](../atl/atl-com-desktop-components.md)

