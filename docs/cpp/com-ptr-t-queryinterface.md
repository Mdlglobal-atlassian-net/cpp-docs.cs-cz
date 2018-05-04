---
title: _com_ptr_t::QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c046f1b1d14b7e7dbd44ca9f5f012e632efef6e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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