---
title: "gslice_array – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::gslice_array
dev_langs: C++
helpviewer_keywords: gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bec570f3a1b0c2ddd8454935b5cfd26e2a217da0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gslicearray-class"></a>gslice_array – třída
Třídu interní, pomocného šablony, která podporuje objekty obecné řez tím, že poskytuje mezi poli podmnožina definované obecné řezy valarray – operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type>  
class gslice_array : public gsplice {  
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
 Třída popisuje objekt, který ukládá odkaz na objekt **va** třídy [valarray –](../standard-library/valarray-class.md)**\<typ >**, společně s objekt **gs**  třídy [gslice](../standard-library/gslice-class.md) které popisuje pořadí prvků pro výběr **valarray –\<typ >** objektu.  
  
 Můžete vytvořit **gslice_array\<typ >** objekt pouze napsáním výrazu ve formátu [va &#91; gs &#93;](../standard-library/valarray-class.md#op_at). Členské funkce tříd gslice_array pak chovat jako odpovídající funkce podpisy definované pro **valarray –\<typ >**kromě toho, že má vliv jenom pořadí vybraných elementů.  
  
 Šablony třídy je nepřímo vytvořené určité valarray – operace a nelze použít přímo v aplikaci. Třídu vnitřní šablonu pomocné místo toho je používán operátor dolního indexu řez:  
  
 `gslice_array`\<**Typ** >  `valarray` \< **typ**>:: `operator[]` ( **constgslice &**).  
  
 Můžete vytvořit **gslice_array\<typ >** objekt pouze napsáním výrazu ve formátu **va [gsl]**, pro řez **gsl** z valarray –  **Va**. Členské funkce tříd gslice_array pak chovat jako odpovídající funkce podpisy definované pro **valarray –\<typ >**kromě toho, že má vliv jenom pořadí vybraných elementů. Pořadí řízené gslice_array je definován třemi parametry konstruktoru řez, index prvním elementem v první řez, počet elementů v každý řez a vzdálenost mezi elementy v každý řez.  
  
 V následujícím příkladu:  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 Indexy musí být platná pro proceduru platná.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [gslice::gslice](../standard-library/gslice-class.md#gslice) příklad toho, jak deklarace a používání slice_array.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<valarray – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
