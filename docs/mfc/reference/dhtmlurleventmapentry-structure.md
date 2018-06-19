---
title: Dhtmlurleventmapentry – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d038fa188ac431f20b0b19ca8ad8bf675943954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370055"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry – struktura
`DHtmlUrlEventMapEntry` Struktura poskytuje podporu mapy událostí více adresy URL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `szUrl`  
 Adresa URL.  
  
 *pEventMap*  
 Mapy událostí přidružené k adrese URL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdhtml.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

