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
ms.openlocfilehash: ee629d9dcffc80ce20306989cad72d466722af87
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123328"
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
 *szUrl*  
 Adresa URL.  
  
 *pEventMap*  
 Mapy událostí přidružené k adrese URL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdhtml.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

