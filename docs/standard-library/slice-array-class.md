---
title: "slice_array – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::slice_array
dev_langs: C++
helpviewer_keywords: slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e87631a98e56adda0f7c6eed172546e9f17f45b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="slicearray-class"></a>slice_array – třída
Třídu interní, pomocného šablony, která podporuje objekty řez tím, že poskytuje operace mezi poli podmnožina definované řezy valarray –.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type>  
class slice_array : public slice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
    void operator=(const Type& x) const;

 
    void operator*=(const valarray<Type>& x) const;

 
    void operator/=(const valarray<Type>& x) const;

 
    void operator%=(const valarray<Type>& x) const;

 
    void operator+=(const valarray<Type>& x) const;

 
    void operator-=(const valarray<Type>& x) const;

 
    void operator^=(const valarray<Type>& x) const;

 
    void operator&=(const valarray<Type>& x) const;

 
    void operator|=(const valarray<Type>& x) const;

 
    void operator<<=(const valarray<Type>& x) const;

 
    void operator>>=(const valarray<Type>& x) const;

 
// The rest is private or implementation defined  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Třída popisuje objekt, který ukládá odkaz na objekt třídy [valarray –](../standard-library/valarray-class.md)**\<typ >**, společně s objekt třídy [řez](../standard-library/slice-class.md), které Popisuje pořadí prvků pro výběr **valarray –\<typ >** objektu.  
  
 Šablony třídy je nepřímo vytvořené určité valarray – operace a nelze použít přímo v aplikaci. Třída interní, pomocného šablon, která používá operátor dolního indexu řez:  
  
 `slice_array`\<**Typ**> `valarray`< **typ**:: `operator[]` ( `slice`).  
  
 Můžete vytvořit **slice_array\<typ >** objekt pouze napsáním výrazu ve formátu [va &#91; sl &#93;](../standard-library/valarray-class.md#op_at), pro řez **sl** z valarray – **va**. Členské funkce tříd slice_array pak chovat jako odpovídající funkce podpisy definované pro **valarray –\<typ >**kromě toho, že má vliv jenom pořadí vybraných elementů. Pořadí řízené slice_array je definován třemi parametry konstruktoru řez, index prvním elementem v řez, počet elementů a vzdálenost mezi elementy. Vyjmout slice_array z valarray – **va** deklarovaná **va**[ `slice`(2, 5, 3)] vybere prvky s indexy 2, 5, 8, 11 a 14 z **va**. Indexy musí být platná pro proceduru platná.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [slice::slice](../standard-library/slice-class.md#slice) příklad toho, jak deklarace a používání slice_array.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<valarray – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
