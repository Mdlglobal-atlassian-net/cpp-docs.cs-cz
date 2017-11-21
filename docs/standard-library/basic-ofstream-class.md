---
title: "basic_ofstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs: C++
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6fa5bdad26039217a52c480d747d3dac1ba2db5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="basicofstream-class"></a>basic_ofstream – třída
Popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementy typu `Elem`, jejichž Určuje vlastnosti znak v třídě `Tr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ofstream : public basic_ostream<Elem, Tr>
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 Základní prvek vyrovnávací paměti souboru.  
  
 `Tr`  
 Vlastnosti základní elementu vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).  
  
## <a name="remarks"></a>Poznámky  
 Když `wchar_t` specializace `basic_ofstream` zapisuje do souboru, pokud je soubor otevřít v režimu textových zapíše MBCS pořadí. Interního vyjádření použije vyrovnávací paměti `wchar_t` znaků.  
  
 Objekt uloží objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `basic_ofstream` objektu a zápis textu do ní.  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_ofstream –](#basic_ofstream)|Vytvoří objekt typu `basic_ofstream`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Zavřete](#close)|Zavře soubor.|  
|[is_open –](#is_open)|Určuje, zda je soubor otevřít.|  
|[Otevřete](#open)|Otevře soubor.|  
|[rdbuf –](#rdbuf)|Vrátí adresu vyrovnávací paměti uložené datového proudu.|  
|[swap](#swap)|Obsah tohoto Exchange `basic_ofstream` pro obsah ze zadaných `basic_ofstream`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí přiřazení zahrnující `rvalue reference` , nenechává kopie za sebou.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<fstream >  
  
 **Namespace:** – std  
  
##  <a name="basic_ofstream"></a>basic_ofstream::basic_ofstream  
 Vytvoří objekt typu `basic_ofstream`.  
  
```
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Název souboru, který se otevřít.  
  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Výchozí soubor otevírání ochrany, odpovídá `shflag` parametr v [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
 `right`  
 Deklarátor odkazu na `basic_ofstream` objekt používaný k inicializaci to `basic_ofstream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), kde **sb** je objekt uložené třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Také inicializuje **sb** voláním `basic_filebuf` <  `Elem`, `Tr`>.  
  
 Druhý a třetí konstruktory inicializuje základní třídu voláním `basic_ostream`( **sb**). Také inicializuje **sb** voláním `basic_filebuf` <  `Elem`, `Tr`> a potom **sb**. [Otevřete](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Pokud pozdější funkce vrátí hodnotu null. ukazatel, volá konstruktor [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
 Čtvrtý konstruktor je funkci kopírování. Se inicializuje objekt s obsahem `right`, považován za deklarátor odkazu.  
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje, jak vytvořit `basic_ofstream` objektu a zápis textu do ní.  
  
```  
// basic_ofstream_ctor.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("C:\\ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
##  <a name="close"></a>basic_ofstream::Close  
 Zavře soubor.  
  
```
void close();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [rdbuf –](../standard-library/basic-ifstream-class.md#rdbuf)**->**[zavřete](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá **zavřete**.  
  
##  <a name="is_open"></a>basic_ofstream::is_open  
 Určuje, zda je soubor otevřít.  
  
```
bool is_open() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je soubor otevřený `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [rdbuf –](#rdbuf)  **->**  [is_open –](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_ofstream_is_open.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   ifstream file;  
   // Open and close with a basic_filebuf  
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );  
   file.close( );  
   if (file.is_open())  
      cout << "it's open" << endl;  
   else  
      cout << "it's closed" << endl;  
}  
```  
  
##  <a name="open"></a>basic_ofstream::Open  
 Otevře soubor.  
  
```
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
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
 Volání členských funkcí [rdbuf –](#rdbuf)  **->**  [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`). Pokud tento funkce vrátí ukazatel s hodnotou null, funkce volá [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) pro příklad, který používá **otevřete**.  
  
##  <a name="op_eq"></a>basic_ofstream::Operator =  
 Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí přiřazení zahrnující `rvalue reference` , nenechává kopie za sebou.  
  
```
basic_ofstream& operator=(basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Rvalue odkaz na `basic_ofstream` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `*this`.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahradí obsah objektu s použitím obsah `right`, považován za deklarátor odkazu.  
  
##  <a name="rdbuf"></a>basic_ofstream::rdbuf  
 Vrátí adresu vyrovnávací paměti uložené datového proudu.  
  
```
basic_filebuf<Elem, Tr> *rdbuf() const
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu vyrovnávací paměti uložené datového proudu.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.  
  
##  <a name="swap"></a>basic_ofstream::swap  
 Výměny obsahu dvou `basic_ofstream` objekty.  
  
```
void swap(basic_ofstream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `lvalue` Odkaz na jiný `basic_ofstream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce výměny obsah tohoto objektu pro obsah `right`.  
  
## <a name="see-also"></a>Viz také  
 [basic_ostream – třída](../standard-library/basic-ostream-class.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



