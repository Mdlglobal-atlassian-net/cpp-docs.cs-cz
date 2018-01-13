---
title: _com_ptr_t::QueryInterface | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs: C++
helpviewer_keywords: QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21dffde38e58bb7c07a1a92421d3febe10cc1032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Konkrétní Microsoft**  
  
 Volání `QueryInterface` členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 **Identifikátory IID** z ukazatele rozhraní.  
  
 `p`  
 Ukazatel nezpracovaná rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Volání **IUnknown::QueryInterface** na ukazatel zapouzdřené rozhraní se zadaným **IID** a vrátí výsledný ukazatel nezpracovaná rozhraní v `p`. Tato rutina indikuje úspěch nebo neúspěch pomocí hodnoty `HRESULT`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)