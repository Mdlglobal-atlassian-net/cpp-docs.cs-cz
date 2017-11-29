---
title: "C3138 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3138
dev_langs: C++
helpviewer_keywords: C3138
ms.assetid: 364ee9e8-9358-410e-bd35-9c4a226a3753
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ba06bed1ce02c8a3030720152892e0e35760afa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3138"></a>C3138 chyby kompilátoru
'rozhraní': 'atribut' rozhraní musí dědit z IDispatch nebo z rozhraní, které dědí z IDispatch  
  
 Rozhraní s [duální](../../windows/dual.md) nebo [dispinterface](../../windows/dispinterface.md) atributy nemá `IDispatch` jako přímý nebo nepřímý základní rozhraní.  
  
 Následující příklad generuje C3138:  
  
```  
// C3138.cpp  
#include <unknwn.h>  
  
[ object, uuid("77ac9240-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyCustomInterface  
{  
   HRESULT mf1(void);  
};  
  
[ dispinterface, uuid("3536f8a0-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDispInterface : IUnknown  
{  
   [id(1)] HRESULT mf2(void);  
};  
  
[ object, dual, uuid("34e90a10-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDualInterface : IMyCustomInterface  // C3138 expected  
{  
   HRESULT mf3(void);  
};  
```