---
title: "moneypunct_byname – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmon/std::moneypunct_byname
dev_langs: C++
helpviewer_keywords: moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fd5c4774da1ea1c0afc25e1538351dad4decbe6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname – třída
Třídu odvozenou šablony, která popisuje objekt, který může sloužit jako `moneypunct` omezující vlastnosti daného národního prostředí, povolení formátování peněžní vstupní pole nebo polí peněžní výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```  
  
## <a name="remarks"></a>Poznámky  
 Její chování je dáno s názvem národní prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, mezinárodní > ( `_Refs`).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



