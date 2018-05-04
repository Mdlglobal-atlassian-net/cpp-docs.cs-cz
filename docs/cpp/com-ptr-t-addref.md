---
title: _com_ptr_t::AddRef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54a1b629f254bae2b72790546bcbb00185f2c44c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Konkrétní Microsoft**  
  
 Volání `AddRef` členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Volání `IUnknown::AddRef` na ukazatel zapouzdřené rozhraní, vyvolání `E_POINTER` chyby, pokud je ukazatel **NULL**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)