---
title: "fpos – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
dev_langs: C++
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0647a5d4a9720b5628d5d540f055013bd40b8b30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fpos-class"></a>fpos – třída
Šablony třídy popisuje objekt, který může ukládat všechny informace potřebné k obnovení indikátor libovolný pozice souboru v rámci všech datového proudu. Objekt fpos – třída\< **St**> efektivně ukládá aspoň dva objekty člen:  
  
-   Posun bajtů, typu [streamoff](../standard-library/ios-typedefs.md#streamoff).  
  
-   Převod stavu, pro použití v objektu basic_filebuf – třída typu **St**, obvykle `mbstate_t`.  
  
 Také může uložit pozice libovolného souboru, pro použití v objektu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md), typu `fpos_t`. Pro prostředí s omezenou soubor velikost, ale `streamoff` a `fpos_t` může být někdy používají zcela zaměnitelným významem. Pro prostředí s žádné datové proudy, které mají kódování závislé na stav `mbstate_t` může ve skutečnosti se nepoužívá. Proto počet členských objektů uložená se může lišit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Statetype>  
class fpos  
```  
  
#### <a name="parameters"></a>Parametry  
 *Statetype*  
 Stavové informace.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[fpos](#fpos)|Vytvořte objekt, který obsahuje informace o pozice (posun) v datovém proudu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[seekpos –](#seekpos)|Standardní knihovna C++ pouze používá interně. Tato metoda není volána z vašeho kódu.|  
|[Stav](#state)|Nastaví nebo vrátí stav převodu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator!=](#op_neq)|Pozice souboru indikátory testy nerovnost.|  
|[operátor +](#op_add)|Zvýší na ukazatel pozice souboru.|  
|[+= – operátor](#op_add_eq)|Zvýší na ukazatel pozice souboru.|  
|[Operator –](#operator-)|Snižuje pozice souboru indikátoru.|  
|[-= – operátor](#operator-_eq)|Snižuje pozice souboru indikátoru.|  
|[Operator ==](#op_eq_eq)|Pozice souboru indikátory testování rovnosti.|  
|[streamoff – operátor](#op_streamoff)|Přetypování typu objektu `fpos` na objekt typu `streamoff`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<ios >  
  
 **Namespace:** – std  
  
##  <a name="fpos"></a>fpos::fpos  
 Vytvořte objekt, který obsahuje informace o pozice (posun) v datovém proudu.  
  
```  
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Posun do datového proudu.  
  
 `_State`  
 Počáteční stav `fpos` objektu.  
  
 *_Filepos*  
 Posun do datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor ukládá posun `_Off`, relativní na začátek souboru a ve stavu počáteční převodu (pokud, záleží). Pokud `_Off` je -1, výsledný objekt představuje pozici neplatný datový proud.  
  
 Druhý konstruktor ukládá nulové posunutí a objekt `_State`.  
  
##  <a name="op_neq"></a>fpos::Operator! =  
 Pozice souboru indikátory testy nerovnost.  
  
```  
bool operator!=(const fpos<Statetype>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Pozice souboru indikátoru vůči kterému chcete porovnat.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud indikátory pozice souboru nejsou stejné, jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `!(*this == right)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// fpos_op_neq.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   fpos<int> pos1, pos2;  
   ifstream file;  
   char c;  
  
   // Compare two fpos object  
   if ( pos1 != pos2 )  
      cout << "File position pos1 and pos2 are not equal" << endl;  
   else  
      cout << "File position pos1 and pos2 are equal" << endl;  
  
   file.open( "fpos_op_neq.txt" );  
   file.seekg( 0 );   // Goes to a zero-based position in the file  
   pos1 = file.tellg( );  
   file.get( c);  
   cout << c << endl;  
  
   // Increment pos1  
   pos1 += 1;  
   file.get( c );  
   cout << c << endl;  
  
   pos1 = file.tellg( ) - fpos<int>( 2);  
   file.seekg( pos1 );  
   file.get( c );  
   cout << c << endl;  
  
   // Increment pos1  
   pos1 = pos1 + fpos<int>( 1 );  
   file.get(c);  
   cout << c << endl;  
  
   pos1 -= fpos<int>( 2 );  
   file.seekg( pos1 );  
   file.get( c );  
   cout << c << endl;  
  
   file.close( );  
}  
```  
  
##  <a name="op_add"></a>fpos::Operator +  
 Zvýší na ukazatel pozice souboru.  
  
```  
fpos<Statetype> operator+(streamoff _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Posun, podle kterého chcete zvýšit indikátoru pozice souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice v souboru.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu **fpos (\*to) +=** `_Off`.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor! =](#op_neq) pro ukázkové použití `operator+`.  
  
##  <a name="op_add_eq"></a>fpos::Operator +=  
 Zvýší na ukazatel pozice souboru.  
  
```  
fpos<Statetype>& operator+=(streamoff _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Posun, podle kterého chcete zvýšit indikátoru pozice souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice v souboru.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce přidá `_Off` uložené posunutí člen objektu a vrátí  **\*to**. Pro umístění v souboru, výsledkem je obecně platná pouze pro binární datové proudy, které nemají stav závislé kódování.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor! =](#op_neq) pro ukázkové použití `operator+=`.  
  
##  <a name="fpos__operator-"></a>fpos::Operator-  
 Snižuje pozice souboru indikátoru.  
  
```  
streamoff operator-(const fpos<Statetype>& right) const;
 
fpos<Statetype> operator-(streamoff _Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Pozice v souboru.  
  
 `_Off`  
 Posun datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první členská funkce `(streamoff)*this - (streamoff) right`. Vrátí druhou členská funkce `fpos(*this) -= _Off`.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor! =](#op_neq) pro ukázkové použití `operator-`.  
  
##  <a name="fpos__operator-_eq"></a>fpos::Operator-=  
 Snižuje pozice souboru indikátoru.  
  
```  
fpos<Statetype>& operator-=(streamoff _Off);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Posun datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Členské funkce vrátí hodnotu `fpos(*this) -= _Off`.  
  
### <a name="remarks"></a>Poznámky  
 Pro umístění v souboru, výsledkem je obecně platná pouze pro binární datové proudy, které nemají stav závislé kódování.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor! =](#op_neq) pro ukázkové použití `operator-=`.  
  
##  <a name="op_eq_eq"></a>fpos::Operator ==  
 Pozice souboru indikátory testování rovnosti.  
  
```  
bool operator==(const fpos<Statetype>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Pozice souboru indikátoru vůči kterému chcete porovnat.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud indikátory pozice souboru jsou stejné jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `(streamoff)*this == (streamoff)right`.  
  
### <a name="example"></a>Příklad  
  V tématu [operátor! =](#op_neq) pro ukázkové použití `operator+=`.  
  
##  <a name="op_streamoff"></a>fpos::Operator streamoff  
 Typ objektu `fpos` na objekt typu `streamoff`.  
  
```  
operator streamoff() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrací uložené posunutí člena objekt a všechny další posun uložené jako součást `fpos_t` člen objektu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// fpos_op_streampos.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   streamoff s;  
   ofstream file( "rdbuf.txt");  
  
   fpos<mbstate_t> f = file.tellp( );  
   // Is equivalent to ..  
   // streampos f = file.tellp( );  
   s = f;  
   cout << s << endl;  
}  
```  
  
```Output  
0  
```  
  
##  <a name="seekpos"></a>fpos::seekpos  
 Tato metoda používá standardní knihovny C++ jen interně. Tato metoda není volána z vašeho kódu.  
  
```  
fpos_t seekpos() const;
```  
  
##  <a name="state"></a>fpos::State  
 Nastaví nebo vrátí stav převodu.  
  
```  
Statetype state() const;

void state(Statetype _State);
```  
  
### <a name="parameters"></a>Parametry  
 `_State`  
 Nový stav převodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Převod stavu.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce člena s hodnotou uloženou v **St** člen objektu. Druhý člen funkce úložiště `_State` v **St** člen objektu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// fpos_state.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main() {  
   using namespace std;  
   streamoff s;  
   ifstream file( "fpos_state.txt" );  
  
   fpos<mbstate_t> f = file.tellg( );  
   char ch;  
   while ( !file.eof( ) )  
      file.get( ch );  
   s = f;  
   cout << f.state( ) << endl;  
   f.state( 9 );  
   cout << f.state( ) << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

