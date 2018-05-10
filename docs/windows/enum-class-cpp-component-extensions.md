---
title: Výčet tříd (C++ Component Extensions) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e17c5e2055ef478dc7cafd5a7b2677f47bb9e074
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="enum-class--c-component-extensions"></a>enum class (rozšíření komponent C++)
Deklaruje výčet v oboru názvů, což je uživatelsky definovaný typ. skládající se z sadu pojmenované konstanty, výčty volat.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Poznámky**  
  
 C + +/ CX a C + +/ CLI podporu `public enum class` a `private enum class` které jsou podobné standardní C++ `enum class` , ale s přidáním systému specifikátor usnadnění. V části **/CLR**, C ++ 11 `enum class` typ je povoleno, ale bude generovat upozornění C4472, která je určena k zajištění, že chcete skutečně typ výčtu ISO a není jazyce C + +/ CX a C + +/ CLI typu. Další informace o standardní C++ ISO `enum` – klíčové slovo, najdete v části [výčty](../cpp/enumerations-cpp.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Syntaxe**  
  
```  
  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **Parametry**  
  
 *Přístup*  
 Usnadnění výčtu, což může být `public` nebo `private`.  
  
 *identifikátor – výčet*  
 Název výčtu.  
  
 *Základní typ*  
 (Volitelné) Základní typ výčtu.  
  
 (Volitelné. Pouze Windows Runtime) s podkladovým typem výčtu, který může být `bool`, `char`, `char16`, `int16`, `uint16`, `int`, `uint32`, `int64`, nebo `uint64`.  
  
 *Enumerátor seznamu*  
 Čárkami oddělený seznam názvů enumerátor.  
  
 Každý enumerátor hodnotu konstantní výraz, který je buď definován implicitně kompilátor, nebo explicitně pomocí notace, *enumerátor*`=`*konstantní výraz*. Ve výchozím nastavení první enumerátor hodnotu nula. Pokud je implicitně definován. Každý další implicitně definované enumerátor hodnotu hodnota předchozí enumerátor + 1.  
  
 *var*  
 (Volitelné) Název proměnné typu výčtu.  
  
 **Poznámky**  
  
 Další informace a příklady naleznete v tématu [výčty](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).  
  
 Všimněte si, že kompilátor vydává chybové zprávy, pokud nemůže být reprezentovaná konstantní výraz, který definuje hodnotu enumerátor *základní typ*.  Kompilátor však nevytváří sestavu chybu pro hodnotu, která neodpovídají základního typu. Příklad:  
  
-   Pokud *základní typ* je numerickou a enumerátor určuje maximální hodnotu pro tento typ, není možné vyjádřit hodnotu Další implicitně definované enumeratoin.  
  
-   Pokud *základní typ* je `bool`, a více než dva výčty jsou implicitně definované výčty po první dvě nelze reprezentovat.  
  
-   Pokud *základní typ* je `char16`a hodnota výčtu rozsahy 0xD800 prostřednictvím 0xDFFF, může být reprezentován hodnota. Hodnota logicky nesprávná, protože představuje poloviční typu Unicode však náhradního pár a neměla by se zobrazit v izolaci.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Syntaxe**  
  
```  
  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **Parametry**  
  
 `access`  
 Usnadnění výčtového typu.  Může být buď **veřejné** nebo `private`.  
  
 `enumerator-list`  
 Čárkami oddělený seznam identifikátorů (výčty) ve výčtu.  
  
 `name`  
 Název výčtu.  Anonymní spravované výčty nejsou povoleny.  
  
 `type` (volitelné)  
 Základní typ *identifikátory*.  To může být jakékoli skalární typu, například podepsaný držitelem nebo bez znaménka verzích int, kratší nebo delší.  `bool` nebo `char` je také povoleno.  
  
 `var` (volitelné)  
 Název proměnné typu výčtu.  
  
 **Poznámky**  
  
 **Výčet tříd** a **enum struct** jsou ekvivalentní deklarace.  
  
 Existují dva typy výčty: spravované nebo C + +/ CX a standard.  
  
 Spravované nebo C + +/ CX výčet může být definovaná následujícím způsobem  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 a je sémanticky ekvivalentní:  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 Standardní výčet může být definovány takto:  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 a je sémanticky ekvivalentní:  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 Spravované enumerátor názvy (*identifikátory*) nejsou vloženy do oboru, kde je definován výčet; všechny odkazy na výčty musí být plně kvalifikovaná (*název* `::` *identifikátor*).  Z tohoto důvodu nelze definovat anonymní spravované výčtu.  
  
 Výčty standardní výčtu jsou důrazně vsunout do nadřazeného oboru.  To znamená pokud existuje jiný symbol se stejným názvem jako enumerátor ve vymezeném oboru, kompilátor dojde k chybě.  
  
 Ve Visual C++ 2002 a Visual C++ 2003 byly vložit výčty slabě (viditelné ve vymezeném oboru Pokud byl jiný identifikátor se stejným názvem).  
  
 Pokud je definována standardní C++ výčtu (bez **– třída** nebo `struct`), kompilace s **/CLR** způsobí, že výčtu sestavují jako spravované výčtu.  Výčet má stále sémantiku nespravované výčtu.  Všimněte si, kompilátor vloží atribut, `Microsoft::VisualC::NativeEnumAttribute`, který rozpoznává – kompilátor Visual C++, k identifikaci pro programátory záměr pro příkaz enum jako nativní výčtu.  Další kompilátory jednoduše zobrazí standardní výčtu jako spravované výčtu.  
  
 S názvem, standard výčtu kompilovat s volbou/CLR se nebude zobrazovat v sestavení jako spravované výčtu a mohou být spotřebovávána jiné spravované kompilátoru.   Nepojmenované standardní výčet však nebudou veřejně viditelný ze sestavení.  
  
 Ve Visual C++ 2002 a Visual C++ 2003, standard výčtu použít jako typ parametr funkce:  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 by emitování následující MSIL pro podpis funkce:  
  
```  
void f(int32);  
```  
  
 V aktuálních verzích kompilátor, ale je standardní výčtu vygenerované jako spravované výčtu [NativeEnumAttribute] a následující MSIL pro podpis funkce:  
  
```  
void f(E)  
```  
  
 Další informace o nativní výčty najdete v tématu [deklarace výčtů C++](../cpp/enumerations-cpp.md).  
  
 Další informace o výčty CLR najdete v tématu:  
  
-   [Podkladový typ výčtového](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 desc  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **Output**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)