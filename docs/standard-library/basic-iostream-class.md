---
title: "basic_iostream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95912a24f3283e66a7f50c06999cf410f428defc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="basiciostream-class"></a>basic_iostream – třída
Datový proud třídu, která můžete provést i vstup a výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje objekt, který řídí vložení prostřednictvím její základní třída [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> a extrakce prostřednictvím její základní třída [basic_ IStream on Request](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Dva objekty sdílejí společné virtuální základní třídu [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Spravují běžné vyrovnávací paměť datového proudu, elementy typu `Elem`, jehož vlastnosti znak určuje třídu `Tr`. Konstruktor inicializuje jeho základních tříd prostřednictvím `basic_istream`( **strbuf**) a `basic_ostream`( **strbuf**).  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream)|Vytvoření `basic_iostream` objektu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[swap](#swap)|Výměny obsah ze zadaných `basic_iostream` objekt pro obsah tohoto objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Přiřadí hodnota zadané `basic_iostream` objekt, který má tento objekt. Jedná se o přesunutí přiřazení zahrnující `rvalue` , nenechává kopie za sebou.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<IStream on Request >  
  
 **Namespace:** – std  
  
##  <a name="basic_iostream"></a>  basic_iostream::basic_iostream  
 Vytvoření `basic_iostream` objektu.  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>Parametry  
 `strbuf`  
 Existující objekt `basic_streambuf`.  
  
 `right`  
 Existující `basic_iostream` objekt, který se používá k vytvoření nové `basic_iostream`.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základních objektech prostřednictvím `basic_istream(strbuf)` a `basic_ostream(strbuf)`.  
  
 Druhý konstruktor inicializuje základních objektech voláním `move(right)`.  
  
##  <a name="op_eq"></a>  basic_iostream::Operator =  
 Přiřazení hodnoty zadané `basic_iostream` objekt, který má tento objekt. Toto je přiřazení přesunutí zahrnující rvalue kopii nenechává za sebou.  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `rvalue` Odkaz na `basic_iostream` objekt, který chcete přiřadit z.  
  
### <a name="remarks"></a>Poznámky  
 Operátor volání člena `swap(right)`.  
  
##  <a name="swap"></a>  basic_iostream::swap  
 Výměny obsah ze zadaných `basic_iostream` objekt pro obsah tohoto objektu.  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `basic_iostream` Objekt, který chcete prohodit.  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí `swap(right)`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

