---
title: "UICheckState – výčet | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afxwinforms/uicheckstate
dev_langs: C++
helpviewer_keywords: uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21b23efdbad9f2b867b104d0a0d9d0bbb4338e5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="uicheckstate-enumeration"></a>UICheckState – výčet
Popisuje, zkontrolujte stav položku uživatelského rozhraní pro příkaz.  
   
### <a name="syntax"></a>Syntaxe   
```  
public enum class 
{  
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]  
   Unchecked,   
   Checked,   
   Indeterminate 
};  
```  
   
### <a name="remarks"></a>Poznámky  
 [ICommandUI::Check](icommandui-interface.md#check) tyto hodnoty používá k popisu stavu položku uživatelského rozhraní.    
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  
