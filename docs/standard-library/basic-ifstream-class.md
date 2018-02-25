---
title: "basic_ifstream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9c923d4c3de5410ac65f9706d875300b0d07cbb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="basicifstream-class"></a>basic_ifstream – třída
Popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementy typu `Elem`, jejichž Určuje vlastnosti znak v třídě `Tr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 Základní prvek vyrovnávací paměti souboru.  
  
 `Tr`  
 Vlastnosti základní elementu vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).  
  
## <a name="remarks"></a>Poznámky  
 Objekt uloží objekt třídy `basic_filebuf` <  `Elem`, `Tr`>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst text ze souboru.  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## <a name="input-basicifstreamclasstxt"></a>Input: basic_ifstream_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## <a name="output"></a>Výstup  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_ifstream](#basic_ifstream)|Inicializuje novou instanci třídy `basic_ifstream` objektu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[close](#close)|Zavře soubor.|  
|[is_open](#is_open)|Určuje, zda je soubor otevřít.|  
|[open](#open)|Otevře soubor.|  
|[rdbuf](#rdbuf)|Vrátí adresu vyrovnávací paměti uložené datového proudu.|  
|[swap](#swap)|Obsah této výměny `basic_ifstream` pro obsah ze zadaných `basic_ifstream`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Přiřadí obsah tohoto objektu datového proudu. Jedná se o přesunutí přiřazení zahrnující `rvalue` , nenechává kopie za sebou.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<fstream >  
  
 **Namespace:** – std  
  
##  <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream  
 Vytvoří objekt typu `basic_ifstream`.  
  
```  
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Název souboru, který se otevřít.  
  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Výchozí soubor otevírání ochrany, odpovídá `shflag` parametr v [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [basic_istream](../standard-library/basic-istream-class.md)( `sb`), kde `sb` je objekt uložené třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Také inicializuje `sb` voláním `basic_filebuf` <  `Elem`, `Tr`>.  
  
 Druhý a třetí konstruktory inicializuje základní třídu voláním `basic_istream`( `sb`). Také inicializuje `sb` voláním [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, pak `sb`. [Otevřete](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Pokud pozdější funkce vrátí hodnotu null. ukazatel, volá konstruktor **setstate –**( `failbit`).  
  
 Čtvrtý konstruktor inicializuje objekt s obsahem `right`, považován za deklarátor odkazu.  
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje, jak načíst text ze souboru. Pokud chcete vytvořit soubor, podívejte se na příklad pro [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).  
  
```  
// basic_ifstream_ctor.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_ctor.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
##  <a name="close"></a>  basic_ifstream::Close  
 Zavře soubor.  
  
```  
void close();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [rdbuf –](#rdbuf)  **->**  [zavřete](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá **zavřete**.  
  
##  <a name="is_open"></a>  basic_ifstream::is_open  
 Určuje, zda je soubor otevřít.  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je soubor otevřený **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [rdbuf –](#rdbuf)  **->**  [is_open –](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) pro příklad, který používá `is_open`.  
  
##  <a name="open"></a>  basic_ifstream::Open  
 Otevře soubor.  
  
```  
void open(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,  
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
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
 Volání členských funkcí [rdbuf –](#rdbuf)  **->**  [otevřete](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; **ios_base::in**). Pokud otevřete selže, volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)( **failbit**), který může vyvolat výjimku ios_base::failure.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) pro příklad, který používá **otevřete**.  
  
##  <a name="op_eq"></a>  basic_ifstream::operator=  
 Přiřadí obsah tohoto objektu datového proudu. Toto je přiřazení přesunutí zahrnující rvalue kopii nenechává za sebou.  
  
```  
basic_ifstream& operator=(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Rvalue odkaz na `basic_ifstream` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `*this`.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahradí obsah objektu s použitím obsah `right`, považován za deklarátor odkazu. Další informace najdete v tématu [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).  
  
##  <a name="rdbuf"></a>  basic_ifstream::rdbuf  
 Vrátí adresu vyrovnávací paměti uložené datového proudu.  
  
```  
basic_filebuf<Elem, Tr> *rdbuf() const 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [basic_filebuf](../standard-library/basic-filebuf-class.md) objektu, který představuje vyrovnávací paměť uložené datového proudu.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pro příklad, který používá `rdbuf`.  
  
##  <a name="swap"></a>  basic_ifstream::swap  
 Výměny obsahu dvou `basic_ifstream` objekty.  
  
```  
void swap(basic_ifstream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odkaz na jiný datový proud vyrovnávací paměti.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce výměny obsah tohoto objektu pro obsah `right`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)


