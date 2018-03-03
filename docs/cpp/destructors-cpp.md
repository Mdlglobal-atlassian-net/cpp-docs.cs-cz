---
title: Destruktory (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37aa5ab5cad2367bfc37e2e1b6fd886540eada8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="destructors-c"></a>Destruktory (C++)
Členské funkce, která je volána automaticky, když objekt ocitne mimo obor nebo je explicitně zničen voláním je destruktor `delete`. Destruktor má stejný název jako třída, před sebou tildou (`~`). Například destruktor třídy `String` je deklarován jako: `~String()`. Pokud nejsou definovány destruktor, kompilátor vám poskytne výchozí jeden; pro mnoho tříd jde dostatečná. Potřebujete definovat vlastní destruktor, když třída uloží obslužné rutiny na systémové prostředky, které je potřeba uvolnit nebo ukazatele, které vlastní paměť ukazovaly na.

Zvažte následující deklaraci třídy `String`:  
  
```  
// spec1_destructors.cpp  
#include <string.h>  
  
class String {  
public:  
   String( char *ch );  // Declare constructor  
   ~String();           //  and destructor.  
private:  
   char    *_text;  
   size_t  sizeOfText;  
};  
  
// Define the constructor.  
String::String( char *ch ) {  
   sizeOfText = strlen( ch ) + 1;  
  
   // Dynamically allocate the correct amount of memory.  
   _text = new char[ sizeOfText ];  
  
   // If the allocation succeeds, copy the initialization string.  
   if( _text )  
      strcpy_s( _text, sizeOfText, ch );  
}  
  
// Define the destructor.  
String::~String() {  
   // Deallocate the memory that was previously reserved  
   //  for this string.  
   if (_text)  
      delete[] _text;  
}  
  
int main() {  
   String str("The piper in the glen...");  
}  
```  
  
 V předchozím příkladu používá destruktor `String::~String` k navrácení paměti dynamicky přidělené pro ukládání textu operátor `delete`.  
  
## <a name="declaring-destructors"></a>Deklarování destruktorů  
 Destruktory jsou funkce se stejným názvem jako třída ale předcházet tildou (`~`)  
  
 Deklarace destruktorů se řídí několika pravidly. Destruktory:  
  
-   Nepřebírají argumenty.  
  
-   Nevrátí hodnotu (nebo `void`).  
  
-   Nelze deklarovat jako **const**, `volatile`, nebo **statické**. Však se může vyvolat pro odstranění objektů deklarován jako **const**, `volatile`, nebo **statické**.  
  
-   Lze deklarovat jako **virtuální**. Použitím virtuálních destruktorů lze zničit objekty bez znalosti jejich typu. Správný destruktor objektu je vyvolán pomocí mechanismu virtuální funkce. Destruktory lze také deklarovat jako čistě virtuální funkce pro abstraktní třídy.  
  
## <a name="using-destructors"></a>Použití destruktorů  
 Destruktory jsou zavolány, pokud dojde k jedné z následujících událostí:  

-   Místní (automatický) objekt s rozsahem bloku se dostane mimo rozsah.  

-   Objekt přidělen s použitím **nové** operátor je explicitně navrácena pomocí **odstranit**.   
  
-   Doba života dočasného objektu skončí.  
  
-   Program se ukončí a globální nebo statické objekty existují.  
  
-   Destruktor je explicitně zavolán pomocí plně kvalifikovaného názvu funkce destruktoru.
  
 Destruktory mohou volně volat členské funkce třídy a přistupovat k datům člena třídy.
  
 Existují dvě omezení pro použití destruktorů:
 - nelze provést jeho adresy
-  odvozené třídy nedědí – destruktor jejich základní třídy.
  
## <a name="order-of-destruction"></a>Pořadí odstranění  
 Pokud objekt ocitne mimo obor nebo je odstranit, posloupnost událostí v jeho dokončení odstraňování vypadá takto:  
  
1.  Třída destruktoru a provede se tělo funkce destruktor.  
  
2.  Destruktory pro nestatické členské objekty se nazývají v obráceném pořadí, ve kterém se zobrazí v deklaraci třídy. Seznam inicializace volitelné členů použité výrobu tito členové nemá vliv na pořadí vytváření nebo odstraňování.   
  
3.  Destruktory pro nevirtuální třídy base se nazývají v obráceném pořadí deklarace.  
  
4.  Destruktory pro virtuální třídy base se nazývají v obráceném pořadí deklarace.  
  
```  
// order_of_destruction.cpp  
#include <stdio.h>  
  
struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };  
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };  
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };  
  
struct B1      { ~B1() { printf("B1 dtor\n"); } };  
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };  
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };  
  
int main() {  
   A1 * a = new A3;  
   delete a;  
   printf("\n");  
  
   B1 * b = new B3;  
   delete b;  
   printf("\n");  
  
   B3 * b2 = new B3;  
   delete b2;  
}  
  
Output: A3 dtor  
A2 dtor  
A1 dtor  
  
B1 dtor  
  
B3 dtor  
B2 dtor  
B1 dtor  
  
```  
  
### <a name="virtual-base-classes"></a>Virtuální základní třídy  
 Destruktory pro virtuální třídy base se nazývají v obráceném pořadí jejich výskytu v necyklicky (hloubku první, zleva doprava, postorder traversal). Následující obrázek znázorňuje dědičnost graf.  
  
 ![Graf dědičnosti, který zobrazuje základní virtuální třídy](../cpp/media/vc392j1.gif "vc392J1")  
Graf dědičnosti základní virtuální třídy  
  
 V následujícím seznamu jsou hlav třída pro třídy vidět na obrázku.  
  
```  
class A  
class B  
class C : virtual public A, virtual public B  
class D : virtual public A, virtual public B  
class E : public C, public D, virtual public B  
```  
  
 K určení pořadí odstranění základní virtuální třídy objektu typu `E`, kompilátor vytvoří seznam použitím následujícím algoritmu:  
  
1.  Procházení grafu vlevo, počínaje nejhlubší bod v grafu (v tomto případě `E`).  
  
2.  Leftward traversals proveďte, dokud navštívili všechny uzly. Poznamenejte si název aktuálního uzlu.  
  
3.  Pokroku v předchozím uzlu (dolů a doprava) a zjistěte, zda je uzel, když si virtuální základní třídy.  
  
4.  Pokud zapamatovaných uzel je virtuální základní třídy, vyhledejte v seznamu zobrazíte, zda je již byla zadána. Pokud není virtuální základní třídy, ji ignorujte.  
  
5.  Pokud zapamatovaných uzel ještě není v seznamu, přidejte ji do dolní části seznamu.  
  
6.  Procházení grafu nahoru a v další cestě vpravo.  
  
7.  Přejděte ke kroku 2.  
  
8.  Při poslední vzestupnou cesta vyčerpání, poznamenejte si název aktuálního uzlu.  
  
9. Přejděte ke kroku 3.  
  
10. Tento proces pokračujte, dokud uzlu dolní opět na aktuální uzel.  
  
 Proto pro třídu `E`, je pořadí odstranění:  
  
1.  Nevirtuální základní třídy `E`.  
  
2.  Nevirtuální základní třídy `D`.  
  
3.  Nevirtuální základní třídy `C`.  
  
4.  Virtuální základní třídy `B`.  
  
5.  Virtuální základní třídy `A`.  
  
 Tento proces vytvoří seřazený seznam jedinečných položek. Žádný název třídy se dvakrát zobrazí. Jakmile je vytvořený v seznamu, je proveden vaši firmu v obráceném pořadí a destruktor pro jednotlivé třídy v seznamu z poslední a první je volána.  
  
 Pořadí vytváření nebo odstraňování je primárně důležité, pokud konstruktory nebo destruktory v jedné třídy závisí na jiné součásti vytváří první nebo zachování již – například pokud destruktor pro `A` (na obrázku výše uvedeném) nedoporučujeme využívat na `B` se stále přítomen, když jeho kód spuštěn, nebo naopak.  
  
 Takové vzájemné závislosti mezi třídami v dědičnost graf jsou ze své podstaty nebezpečné, protože třídy odvozené později změnit, což je krajní levá cesty, a tím změnit pořadí vytváření a odstraňování.  
  
### <a name="nonvirtual-base-classes"></a>Nevirtuální třídy base  
 Destruktory pro nevirtuální třídy base se nazývají v obráceném pořadí, ve které jsou deklarované názvy základních tříd. Vezměte v úvahu následující deklaraci třídy:  
  
```  
class MultInherit : public Base1, public Base2  
...  
```  
  
 V předchozím příkladu destruktor pro `Base2` je volána před provedením destruktor pro `Base1`.  
  
## <a name="explicit-destructor-calls"></a>Explicitní volání destruktoru  
 Explicitní volání destruktoru je zřídka nezbytné. Avšak může být užitečné pro vyčištění objektů umístěných na absolutních adresách. Tyto objekty jsou běžně přidělen s použitím uživatelem definované **nové** operátor, který se použije argument umístění. **Odstranit** operátor nelze navrátit tuto paměť, protože není přidělené z obchodu volné (Další informace najdete v tématu [nové a odstraňte operátory](../cpp/new-and-delete-operators.md)). Volání destruktoru však může provádět odpovídající vyčištění. Chcete-li explicitně zavolat destruktor objektu `s` třídy `String`, použijte jeden z následujících příkazů:  
  
```  
s.String::~String();     // Nonvirtual call  
ps->String::~String();   // Nonvirtual call  
  
s.~String();       // Virtual call  
ps->~String();     // Virtual call  
```  
  
 Zápis explicitního volání destruktorů, ukázaný v předchozím příkladu, lze použít bez ohledu na to, zda typ destruktor definuje. To umožňuje provést explicitní volání bez znalosti, zda je definován destruktor typu. Explicitní volání destruktoru, který není definován, nemá žádný vliv.  
