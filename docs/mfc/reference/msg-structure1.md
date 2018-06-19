---
title: MSG – Struktura1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dbbcdd3404705a9ac7c6c7969a9ebeeb0238f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372254"
---
# <a name="msg-structure1"></a>MSG – Struktura1
`MSG` Struktura obsahuje informace o zpráv z fronty zpráv vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagMSG {     // msg    
    HWND hwnd;  
    UINT message;  
    WPARAM wParam;  
    LPARAM lParam;  
    DWORD time;  
    POINT pt;  
} MSG;  
```  
  
#### <a name="parameters"></a>Parametry  
 *hWnd*  
 Identifikuje okno jejichž procedury okna obdrží zprávu.  
  
 `message`  
 Určuje číslo zprávy.  
  
 `wParam`  
 Určuje další informace o zprávě. Přesný význam závisí na hodnotu **zpráva** člen.  
  
 `lParam`  
 Určuje další informace o zprávě. Přesný význam závisí na hodnotu **zpráva** člen.  
  
 `time`  
 Určuje dobu, kdy byla zpráva vystavena.  
  
 `pt`  
 Určuje pozici kurzoru, v souřadnice obrazovky, když zpráva byla vrácena.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

