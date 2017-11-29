---
title: "ostrstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs: C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42b0786a140cf9657257d7f79a225a0473115282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ostrstream-class"></a>ostrstream – třída
Popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ostrstream : public ostream
```  
  
## <a name="remarks"></a>Poznámky  
 Objekt uloží objekt třídy `strstreambuf`.  
  
> [!NOTE]
>  Tato třída je zastaralá. Zvažte použití [ostringstream –](../standard-library/sstream-typedefs.md#ostringstream) nebo [wostringstream –](../standard-library/sstream-typedefs.md#wostringstream) místo.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[ostrstream –](#ostrstream)|Vytvoří objekt typu `ostrstream`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[zablokování](#freeze)|Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.|  
|[pcount –](#pcount)|Vrátí počet prvků zapsána do řízené sekvenci.|  
|[rdbuf –](#rdbuf)|Vrátí přidruženému ukazatel na datový proud `strstreambuf` objektu.|  
|[str –](#str)|Volání [freeze](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvenci.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<strstream – >  
  
 **Namespace:** – std  
  
##  <a name="freeze"></a>ostrstream::freeze  
 Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Freezeit`  
 A `bool` označující, zda chcete datového proudu k zablokováno.  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [rdbuf –](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).  
  
### <a name="example"></a>Příklad  
  V tématu [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá **freeze**.  
  
##  <a name="ostrstream"></a>ostrstream::ostrstream  
 Vytvoří objekt typu `ostrstream`.  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Vyrovnávací paměti.  
  
 `count`  
 Velikost vyrovnávací paměti v bajtech.  
  
 `_Mode`  
 Režim vstupní a výstupní vyrovnávací paměti. V tématu [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktory inicializovat základní třídu voláním [ostream –](../standard-library/ostream-typedefs.md#ostream)( **sb**), kde **sb** je objekt uložené třídy [strstreambuf](../standard-library/strstreambuf-class.md). První konstruktor inicializuje také **sb** voláním `strstreambuf`. Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:  
  
-   Pokud `_Mode`  &  **ios_base::app**== 0, pak `ptr` musí určit první prvek pole `count` elementy a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   V opačném `ptr` musí určit první prvek pole počet elementů obsahující řetězec C jejichž první prvek je určen podle `ptr`a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
##  <a name="pcount"></a>ostrstream::pcount  
 Vrátí počet prvků zapsána do řízené sekvenci.  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů zapsána do řízené sekvenci.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [rdbuf –](#rdbuf) -> [pcount –](../standard-library/strstreambuf-class.md#pcount).  
  
### <a name="example"></a>Příklad  
  V tématu [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) příklad, který používá `pcount`.  
  
##  <a name="rdbuf"></a>ostrstream::rdbuf  
 Vrátí ukazatel datový proud přidružený strstreambuf objektu.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový proud je související objekt strstreambuf.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [strstreambuf](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Příklad  
  V tématu [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) příklad, který používá `rdbuf`.  
  
##  <a name="str"></a>ostrstream::str  
 Volání [freeze](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvenci.  
  
```
char *str();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátek řízené sekvenci.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [rdbuf –](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).  
  
### <a name="example"></a>Příklad  
  V tématu [strstream::str](../standard-library/strstreambuf-class.md#str) příklad, který používá **str**.  
  
## <a name="see-also"></a>Viz také  
 [ostream –](../standard-library/ostream-typedefs.md#ostream)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)


