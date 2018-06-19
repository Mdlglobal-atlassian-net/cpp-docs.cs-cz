---
title: Sémantika typu hodnoty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44662f2ad8e79712b4aab17e2784a72e01ec4116
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171847"
---
# <a name="value-type-semantics"></a>Sémantika typu hodnoty
Sémantika typu hodnoty změnily ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Tady je typ kanonický jednoduchý hodnoty použít v spravovaných rozšíření pro C++ – specifikace:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 Ve spravovaných rozšíření jsme může mít čtyři syntaktické varianty typu hodnoty (kde forms 2 a 3 jsou stejné sémanticky):  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>Vyvolání zděděných virtuálních metod  
 `Form (1)` je objekt kanonické hodnoty a je to bude přiměřeně správně pochopeny, s výjimkou případů, kdy se někdo pokusí vyvolat zděděnou virtuální metodu, jako `ToString()`. Příklad:  
  
```  
v.ToString(); // error!  
```  
  
 Chcete-li vyvolat tuto metodu, protože není přepsána v `V`, kompilátor musí mít přístup k tabulce přidružené virtuální základní třídy. Protože jsou typy hodnot úložiště ve stavu bez přidruženého ukazatele na jejich virtuální tabulku (vptr), to vyžaduje, aby `v` se do pole. V návrhu spravovaných rozšíření jazyka implicitní zabalení se nepodporuje, ale musí být explicitně určena programátorů, jako v  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 Primární motiv za tento návrh je pedagogický: základní mechanismus musí být viditelná pro programátorů tak, aby porozuměl "ceně" není poskytnout instance v rámci její typ hodnoty. Byly `V` tak, aby obsahovala instanci `ToString`, zabalení nebude nutné.  
  
 Lexikální složitost explicitně zabalení objektu, ale ne podkladová cena zabalení samotného, je odebrána v nové syntaxe:  
  
```  
v.ToString(); // new syntax  
```  
  
 ale za cenu pravděpodobně oklamání návrháře tříd nebyl úspěšný dispozici explicitní instance náklady `ToString` metoda v rámci `V`. Důvod upřednostňují implicitní zabalení je, že zatímco je obvykle pouze jeden návrhář tříd, je neomezený počet uživatelů, z nichž žádný by neměl možnost Upravit `V` eliminovat explicitní pole může být obtížné.  
  
 Kritéria, podle kterých chcete-li zjistit, zda chcete poskytovat přepsání instance `ToString` v rámci hodnoty by měla být třída četnost a umístění jeho použití. Pokud je volána velmi zřídka, je samozřejmě málo výhodné v jeho definice. Podobně pokud je volána v oblastech nenáročných aplikace, její přidání také nepřidá měřitelný výkon obecné na výkon aplikace. Alternativně můžete zachovat sledovací popisovač zabalené hodnotu a volání prostřednictvím tohoto popisovače by nevyžadovalo zabalení.  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Již není výchozí konstruktor hodnotu – třída  
 Další rozdíl s typem hodnotu mezi spravovaných rozšíření a nové syntaxe je odebrání podpory pro výchozí konstruktor. Je to proto, že v určitých případech při provádění modulu CLR ve kterém můžete vytvořit instanci typu hodnota bez vyvolání přidružené výchozí konstruktor. To znamená pokus pod spravovaných rozšíření pro podporu výchozí konstruktor v rámci typu hodnoty může není v praxi zaručit. Zadané této neexistence záruky, bylo považováno za lepší podporu zcela vynechat spíše než ji být nedeterministickou v jeho aplikaci.  
  
 Toto není tak špatně, jak se může zdát původně. Důvodem je, že je automaticky vynulován každý objekt typu hodnoty (každý typ je inicializován na výchozí hodnotu). V důsledku toho jsou členy místní instance nikdy definován. V tomto smyslu ztrátu schopnost definovat triviální výchozí konstruktor není skutečně ke ztrátě všech - a ve skutečnosti je efektivnější, když provádí modulu CLR.  
  
 Problém je, když uživatel spravovaných rozšíření definuje netriviální výchozí konstruktor. Tato akce nemá žádné mapování na nové syntaxe. Kód v konstruktoru bude nutné migrovat do pojmenované inicializační metoda, která by bylo nutné být explicitně volána uživatelem.  
  
 Deklarace objektu typu hodnoty v rámci nové syntaxe je jinak beze změny. Dolů straně tohoto objektu je, že typy hodnot není dostatečné pro zabalení nativních typů z následujících důvodů:  
  
-   Neexistuje žádná podpora pro destruktor v rámci typu hodnoty. To znamená neexistuje žádný způsob, jak automatizovat sadu akcích aktivovaných na konci životnosti objektu.  
  
-   Nativních tříd může obsahovat pouze v rámci spravovaného typu jako ukazatel, který je pak přidělena na nativní haldě.  
  
 Rádi bychom se zabalení malé nativních tříd v typu hodnoty namísto typu odkazu. aby se zabránilo přidělení dvojité haldy: nativní halda k udržování nativního typu a halda CLR pro uložení spravovaná obálka. Zabalení nativních tříd v rámci typu hodnoty lze zabránit spravovaná halda, ale poskytuje způsob, jak automatizovat recyklaci nativní halda paměti. Odkazové typy jsou jediné proveditelné spravované typy v rámci kterých obalit netriviální nativních tříd.  
  
## <a name="interior-pointers"></a>Vnitřních ukazatelů  
 `Form (2)` a `Form (3)` vyšší můžete vyřešit téměř vše v tomto světě nebo další (to znamená, vše spravovaným nebo nativním). Ano, například všechny následující jsou povoleny ve spravovaných rozšíření:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
V *pv = 0;  // Form (2)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0;  // Form (4)  
  
R* r;  
  
pv = &v;            // address a value type on the stack  
pv = __nogc new V;  // address a value type on native heap  
pv = pvgc;          // we are not sure what this addresses  
pv = pvbx;          // address a boxed value type on managed heap  
pv = &r->vr;        // an interior pointer to value type within a  
                    //    reference type on the managed heap  
```  
  
 Ano `V*` můžete vyřešit umístění v místním blokovým (a proto může být dangling) v globálním oboru v rámci nativního haldy (například pokud byl již odstraněn objekt ho adresy), v rámci haldy CLR (a proto budou sledovat, pokud by měl být přemístění během uvolňování paměti) a v rámci vnitřek referenční objekt. v haldě CLR (vnitřní ukazatel, jako to, se říká, také transparentně sledován).  
  
 Ve spravovaných rozšíření, neexistuje žádný způsob, jak oddělit nativní aspekty `V*`; to znamená, v jeho přístupnosti, je považován, která zpracovává možnost jeho adresování objektu nebo určitých podřízených objektů na spravované haldě.  
  
 V nové syntaxe je ukazatel typu hodnoty rozdělen do dvou typů: `V*`, který je omezen na jiný CLR haldy umístění a vnitřní ukazatel `interior_ptr<V>`, který umožňuje, ale nevyžaduje adresu v rámci spravovaná halda.  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)` a `Form (3)` spravovaných rozšíření mapování na `interior_ptr<V>`. `Form (4)` je sledovací popisovač. Zaměřuje se na celý objekt, který byl zabalen v rámci spravovaná halda. Je přeložená v nové syntaxe do `V^`,  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Následující deklarace ve spravovaných rozšíření všechny mapují na vnitřní ukazatele v nové syntaxe. (Jsou typy hodnot v rámci `System` oboru názvů.)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 Předdefinované typy nejsou považovány za spravované typy, přestože slouží jako aliasy pro typů v rámci `System` oboru názvů. Proto následující mapování uložení true mezi spravovaných rozšíření a nové syntaxe:  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 Při překladu `V*` v existující aplikaci, je vždy zapnout nejvíce konzervativní strategií `interior_ptr<V>`. Toto je, jak bylo ošetřeno pod spravovaných rozšíření. V nové syntaxe programátorů má možnost omezení typu hodnoty na jiné spravované haldy adresy zadáním `V*` místo vnitřní ukazatel. Pokud při překladu vašeho programu, můžete provést přechodné uzavření všech jeho použití a ujistěte se, že není přiřazena žádná adresa je v rámci spravovaná halda, pak jej jako ponechat `V*` je v pořádku.  
  
## <a name="pinning-pointers"></a>Přídavné ukazatele  
 Uvolňování paměti může volitelně přesunout objekty, které jsou umístěny v haldě CLR do různých umístění v rámci haldy, obvykle během fáze komprimace. Tento přesun se nejedná o problém pro sledování popisovače, sledovacích odkazů a vnitřních ukazatelů, které aktualizují tyto entity transparentně. Tento přesun je problém, ale pokud uživatel předal adresu objektu v haldě CLR mimo běhové prostředí. Volatile pohyb objektu je v takovém případě může způsobit selhání běhového prostředí. Vyloučení objektů, jako jsou tyto od přesouvání, jsme lokálně připnout na jejich umístění pro jeho použití mimo rozsah.  
  
 Ve spravovaných rozšíření *Připnutí ukazatelů* je deklarovaný s prohlášením `__pin` – klíčové slovo. Tady je příklad mírně liší od specifikace spravovaných rozšíření:  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 V novém návrhu jazyka Připnutí ukazatel deklarován pomocí syntaxe podobá vnitřní ukazatel.  
  
```  
ref struct H  
{  
public:  
   int j;  
};  
  
int main()  
{  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
  
   // ...  
}  
```  
  
 Připnutí ukazatelů podle nové syntaxe je zvláštní případ vnitřního ukazatele. Zůstanou původní omezení na Připnutí ukazatel. Například nelze použít jako parametr nebo návratový typ metody; lze deklarovat pouze u místní objektu. Počet další omezení, ale bylo přidáno v nové syntaxe.  
  
 Výchozí hodnota Připnutí ukazatele je `nullptr`, nikoli `0`. A `pin_ptr<>` nelze inicializovat nebo přiřadit `0`. Všechna přiřazení `0` v existující kód bude nutné změnit tak, aby `nullptr`.  
  
 Přídavný ukazatel pod spravovaných rozšíření bylo povoleno adresovat celý objekt, jako v následujícím příkladu převzat ze spravovaných rozšíření specifikace:  
  
```  
__gc class G {  
public:  
   void incr(int* pi) { pi += 1; }  
};  
__gc struct H { int j; };  
void f( G * g ) {  
   H __pin * pH = new H;     
   g->incr(& pH -> j);     
};  
```  
  
 V nové syntaxe Připnutí celý objekt vrácený `new` výraz není podporován. Místo toho musí být odkazována adresu vnitřního člena. Například  
  
```  
ref class G {  
public:  
   void incr(int* pi) { *pi += 1; }  
};  
ref struct H { int j; };  
void f( G^ g ) {  
   H ^ph = gcnew H;  
   Console::WriteLine(ph->j);  
   pin_ptr<int> pj = &ph->j;  
   g->incr(  pj );  
   Console::WriteLine(ph->j);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Hodnotové typy a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)