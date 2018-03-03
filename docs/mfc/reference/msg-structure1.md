---
title: "MSG – Struktura1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b504f116dcbff7fa45e741ff9715070ee0c74583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

