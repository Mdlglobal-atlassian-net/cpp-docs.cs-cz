---
title: MSG – Struktura1 | Dokumentace Microsoftu
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
ms.openlocfilehash: 5fe629c2f279b6b258f4824229490f7b72b4ce4d
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338809"
---
# <a name="msg-structure1"></a>MSG – Struktura1
`MSG` Struktura obsahuje informace o zprávy z fronty zpráv vlákna.  
  
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
 Identifikuje okno, jehož proceduru okna obdrží zprávu.  
  
 *message*  
 Určuje číslo zprávy.  
  
 *wParam*  
 Určuje další informace o zprávě. Přesné význam závisí na hodnotě `message` člena.  
  
 *lParam*  
 Určuje další informace o zprávě. Přesné význam závisí na hodnotě `message` člena.  
  
 *čas*  
 Určuje dobu, kdy byla publikována zpráva.  
  
 *PT*  
 Určuje pozici kurzoru v souřadnicovém systému obrazovky, když byla publikována zpráva.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

