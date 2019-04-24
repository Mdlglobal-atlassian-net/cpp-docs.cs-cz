---
title: DHtmlUrlEventMapEntry – struktura
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c9b58067a9c8b6a71cd22b654a2f82ba0f8bfe36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322732"
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

**Header:** afxdhtml.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
