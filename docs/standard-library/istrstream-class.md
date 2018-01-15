---
title: "istrstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs: C++
helpviewer_keywords: istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e3e91e809980f32c839497ac13b4641bf72c8a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="istrstream-class"></a>istrstream – třída
Popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```
class istrstream : public istream
```  
  
## <a name="remarks"></a>Poznámky  
 Objekt uloží objekt třídy `strstreambuf`.  
  
> [!NOTE]
>  Tato třída je zastaralá. Zvažte použití [istringstream –](../standard-library/sstream-typedefs.md#istringstream) nebo [wistringstream –](../standard-library/sstream-typedefs.md#wistringstream) místo.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[istrstream –](#istrstream)|Vytvoří objekt typu `istrstream`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[rdbuf –](#rdbuf)|Vrátí přidruženému ukazatel na datový proud `strstreambuf` objektu.|  
|[str –](#str)|Volání [freeze](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvenci.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<strstream – >  
  
 **Namespace:** – std  
  
##  <a name="istrstream"></a>istrstream::istrstream  
 Vytvoří objekt typu `istrstream`.  
  
```
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Délka vyrovnávací paměti ( `ptr`).  
  
 `ptr`  
 Obsah, se kterými je inicializován vyrovnávací paměti.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory inicializovat základní třídu voláním [IStream on Request](../standard-library/istream-typedefs.md#istream)( **sb**), kde **sb** je objekt uložené třídy [strstreambuf](../standard-library/strstreambuf-class.md) . První dva konstruktory také inicializovat **sb** voláním `strstreambuf`(( **const** `char` \*) `ptr`, 0). Místo toho volat zbývající dva konstruktory `strstreambuf`(( **const** `char` *) `ptr`, `count` ).  
  
##  <a name="rdbuf"></a>istrstream::rdbuf  
 Vrátí ukazatel datový proud přidružený strstreambuf objektu.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový proud je související objekt strstreambuf.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí adresu vyrovnávací paměti uložené datového proudu, typ ukazatele na [strstreambuf](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Příklad  
  V tématu [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) příklad, který používá `rdbuf`.  
  
##  <a name="str"></a>istrstream::str  
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
 [IStream on Request](../standard-library/istream-typedefs.md#istream)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



