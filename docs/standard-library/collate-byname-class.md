---
title: "collate_byname – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: locale/std::collate_byname
dev_langs: C++
helpviewer_keywords: collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 317160860374678f35b8ea7e883db7afe45fdf38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="collatebyname-class"></a>collate_byname – třída
Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost kolace daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast v případě konvencí řazení řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>Parametry  
 `_Locname`  
 S názvem národní prostředí.  
  
 `_Refs`  
 Počet počáteční odkazů.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) typu [collate](../standard-library/collate-class.md#collate)\<CharType >. Je dáno jeho chování [s názvem](../standard-library/locale-class.md#name) národního prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [collate](../standard-library/collate-class.md#collate)\<CharType > ( `_Refs`).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


