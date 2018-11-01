---
title: DHtmlUrlEventMapEntry – struktura
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: 0a1dc86080c094a7ac89940cd43a8edac973e10c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431626"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry – struktura

`DHtmlUrlEventMapEntry` Struktura zajišťuje podpora mapy událostí více adres URL.

## <a name="syntax"></a>Syntaxe

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>Parametry

*szUrl*<br/>
Adresa URL.

*pEventMap*<br/>
Mapa událostí přidružené k adrese URL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

