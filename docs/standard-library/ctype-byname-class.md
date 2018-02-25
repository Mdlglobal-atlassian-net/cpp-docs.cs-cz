---
title: "ctype_byname – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocale/std::ctype_byname
dev_langs:
- C++
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9163ddcb30d1c79bb8e69240702423f27130f0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ctypebyname-class"></a>ctype_byname – třída
Třída odvozená šablony popisuje objekt, který může sloužit jako ctype omezující vlastnosti daného národního prostředí, povolení klasifikace znaků a převod znaků mezi případ a nativní a národní prostředí zadaný znakových sad.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```  
  
## <a name="remarks"></a>Poznámky  
 Její chování je dáno s názvem národní prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [ctype](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) nebo jeho ekvivalent pro základní třídu `ctype<char>`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



