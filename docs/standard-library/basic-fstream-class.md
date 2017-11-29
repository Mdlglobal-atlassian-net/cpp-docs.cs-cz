---
title: "basic_fstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
dev_langs: C++
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f4c174050d2280f116f41be94741dc3c71ae91a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="basicfstream-class"></a>basic_fstream – třída
Popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementy typu `Elem`, jehož vlastnosti znak určuje třídu `Tr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_fstream : public basic_iostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 Základní prvek vyrovnávací paměti souboru.  
  
 `Tr`  
 Vlastnosti základní elementu vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).  
  
## <a name="remarks"></a>Poznámky  
 Objekt uloží objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.  
  
> [!NOTE]
>  Ukazatel get a put ukazatele objektu fstream **není** nezávisle na sobě navzájem. Pokud se přesune ukazatel get, takže nemá put ukazatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `basic_fstream` objekt, který může číst z a zapisovat do.  
  
```  
// basic_fstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);  
    if (!fs.bad())  
    {  
        // Write to the file.  
        fs << "Writing to a basic_fstream object..." << endl;  
        fs.close();  
  
        // Dump the contents of the file to cout.  
        fs.open("fstream.txt", ios::in);  
        cout << fs.rdbuf();  
        fs.close();  
    }  
}  
```  
  
```Output  
Writing to a basic_fstream object...  
```  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_fstream –](#basic_fstream)|Vytvoří objekt typu `basic_fstream`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Zavřete](#close)|Zavře soubor.|  
|[is_open –](#is_open)|Určuje, zda je soubor otevřít.|  
|[Otevřete](#open)|Otevře soubor.|  
|[rdbuf –](#rdbuf)|Vrátí adresu vyrovnávací paměti uložené datového proudu, typ ukazatele na [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|  
|[swap](#swap)|Obsah tohoto objektu s obsahem jiného výměny `basic_fstream` objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<fstream >  
  
 **Namespace:** – std  
  
##  <a name="basic_fstream"></a>basic_fstream::basic_fstream  
 Vytvoří objekt typu `basic_fstream`.  
  
```  
basic_fstream();

explicit basic_fstream(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in | ios_base::out,  
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in | ios_base::out,  
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Název souboru, který se otevřít.  
  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Výchozí soubor otevírání ochrany, odpovídá `shflag` parametr v [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**), kde **sb** je objekt uložené třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Také inicializuje **sb** voláním `basic_filebuf` \< **Elem**, **Tr**>.  
  
 Druhý a třetí konstruktory inicializuje základní třídu voláním `basic_iostream`( **sb**). Také inicializuje **sb** voláním `basic_filebuf` \< **Elem**, **Tr**> a potom **sb.** [ Otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Pokud pozdější funkce vrátí hodnotu null. ukazatel, volá konstruktor [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
 Čtvrtý konstruktor inicializuje objekt s obsahem `right`, považován za deklarátor odkazu.  
  
### <a name="example"></a>Příklad  
  V tématu [streampos](../standard-library/ios-typedefs.md#streampos) pro příklad, který používá `basic_fstream`.  
  
##  <a name="close"></a>basic_fstream::Close  
 Zavře soubor.  
  
```  
void close();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [rdbuf –](#rdbuf)  **->**  [zavřete](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad použití **zavřete**.  
  
##  <a name="is_open"></a>basic_fstream::is_open  
 Určuje, zda je soubor otevřít.  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je soubor otevřený **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [rdbuf –](#rdbuf)**->**[is_open –](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) příklad použití `is_open`.  
  
##  <a name="open"></a>basic_fstream::Open  
 Otevře soubor.  
  
```  
void open(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in | ios_base::out,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,  
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in | ios_base::out,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Název souboru, který se otevřít.  
  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Výchozí soubor otevírání ochrany, odpovídá `shflag` parametr v [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [rdbuf –](#rdbuf)  **->**  [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Pokud tento funkce vrátí ukazatel s hodnotou null, funkce volá [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) příklad použití **otevřete**.  
  
##  <a name="op_eq"></a>basic_fstream::Operator =  
 Přiřadí k tomuto objektu obsah z objektu zadaného datového proudu. Toto je přesunout přiřazení, který zahrnuje rvalue kopii nenechává za sebou.  
  
```  
basic_fstream& operator=(basic_fstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odkaz na lvalue `basic_fstream` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `*this`.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahradí obsah objektu s použitím obsah `right`, považován za deklarátor odkazu.  
  
##  <a name="rdbuf"></a>basic_fstream::rdbuf  
 Vrátí adresu vyrovnávací paměti uložené datového proudu, typ ukazatele na [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>.  
  
```  
basic_filebuf<Elem, Tr> *rdbuf() const 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa vyrovnávací paměti uložené datového proudu.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) příklad použití `rdbuf`.  
  
##  <a name="swap"></a>basic_fstream::swap  
 Výměny obsahu dvou `basic_fstream` objekty.  
  
```  
void swap(basic_fstream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `lvalue` Odkaz na `basic_fstream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce výměny obsah tohoto objektu a obsah `right`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)
