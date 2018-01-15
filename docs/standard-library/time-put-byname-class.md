---
title: "time_put_byname – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xloctime/std::time_put_byname
dev_langs: C++
helpviewer_keywords: time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a03cfd4b8f8b1d199cd7a3f613bed8717c1910e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="timeputbyname-class"></a>time_put_byname – třída
Třída odvozená šablony popisuje objekt, který může sloužit jako národní prostředí omezující vlastnost typu `time_put` \< CharType, OutputIterator >.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```  
  
#### <a name="parameters"></a>Parametry  
 `_Locname`  
 Název národního prostředí.  
  
 `_Refs`  
 Počet počáteční odkazů.  
  
## <a name="remarks"></a>Poznámky  
 Je dáno jeho chování [s názvem](../standard-library/locale-class.md#name) národního prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > ( `_Refs`).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



