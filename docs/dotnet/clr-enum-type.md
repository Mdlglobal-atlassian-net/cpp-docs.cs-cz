---
title: Typ výčtu CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2416a306373db08c5e925b4987fc8a9273973c39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111494"
---
# <a name="clr-enum-type"></a>Typ enum v prostředí CLR
Deklarace a chování výčty změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Deklarace výčtu spravovaných rozšíření předchází `__value` – klíčové slovo. Rada tady je rozlišení je nativní výčet z výčtu CLR, které je odvozeno z `System::ValueType`, při které naznačují podobá funkce. Příklad:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 Nové syntaxe řeší problém rozlišování nativní a výčty CLR tím, že zdůraznění třída povaha k tomu spíše než jeho kořeny typ hodnoty. Jako takový `__value` zrušené – klíčové slovo, nahradí dvojice klíčový slova `enum class`. To poskytuje spárované – klíčové slovo symetrie deklaracích odkaz, hodnotu a rozhraní třídy:  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 Překlad dvojic výčtu `e1` a `e2` v nové syntaxe vypadá takto:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Kromě této malé syntaktické změny chování výčtového typu CLR byl změněn v mnoha různými způsoby:  
  
-   Dopředná deklarace výčtu CLR není podporován. Neexistuje žádné mapování. Je jednoduše označení chyby kompilace.  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   Rozlišení přetížení mezi vestavěné typy aritmetické a `Object` hierarchie tříd má obrácený mezi dvěma jazykové verze! Jako vedlejší účinek jsou CLR výčty už implicitně převedena na aritmetické typy.  
  
-   V nové syntaxe výčtu CLR udržuje vlastní obor, což není velká písmena v spravovaných rozšíření. Dříve byly výčty viditelné v rámci oboru obsahujícího výčtového typu. Nyní jsou výčty zapouzdřený v rámci oboru výčtového typu.  
  
## <a name="clr-enums-are-a-kind-of-object"></a>Výčty CLR jsou objekt druh  
 Předpokládejme následující fragment kódu:  
  
```  
__value enum status { fail, pass };  
  
void f( Object* ){ Console::WriteLine("f(Object)\n"); }  
void f( int ){ Console::WriteLine("f(int)\n"); }  
  
int main()  
{  
   status rslt = fail;  
  
   f( rslt ); // which f is invoked?  
}  
```  
  
 Pro nativní programátora jazyka C++ přirozeném odpověď na otázku, kterou instanci systému přetížené `f()` je volána, je `f(int)`. Výčet je symbolický integrální konstanta a je součástí standardní integrální reklamní akce, které mají přednost před v tomto případě.  A ve skutečnosti ve spravovaných rozšíření, to byla instance, ke které se přeloží volání. Příčinou počet výskyt nečekaných událostí - ne v případě, že jsme použili je nativní C++ rámce nezapomeňte of – ale potřeby jsme je pro interakci s existující framework BCL (základní třída knihovna), kde `Enum` je třída nepřímo odvozený od `Object`. V návrhu jazyka Visual C++, instanci `f()` vyvolat je u `f(Object^)`.  
  
 Způsob, jakým Visual C++ se rozhodli vynutit je tak, aby nepodporoval implicitní převody mezi typem výčtu CLR a aritmetické typy. To znamená, že všechny přiřazení objektu typu výčtu CLR na typ aritmetické bude vyžadovat explicitní přetypování. Ano například uděleno  
  
```  
void f( int );  
```  
  
 jako metodu přetížený, v spravovaných rozšíření volání  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 je ok a hodnota obsažené v `rslt` je implicitně převést na celočíselnou hodnotu. V jazyce Visual C++ toto volání se nepovede zkompilovat. Chcete-li správně přeložit, jsme třeba vložit operátora převodu:  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## <a name="the-scope-of-the-clr-enum-type"></a>Obor typu výčtu CLR  
 Jednu z těchto změn mezi jazyky C a C++ se přidání v jazyce C++ oboru v rámci struktura zařízení. Struktury v jazyce C, je právě data agregační bez podpory rozhraní nebo přidruženého oboru. To bylo poměrně znak změnu v době a sporné problém pro mnoho nových C++ uživatelů pocházejících z jazyka C. Vztah mezi nativní a výčtu CLR se podobá je.  
  
 Ve spravovaném rozšíření byl proveden pokus o definujte slabě vloženého názvy pro výčty z výčtu CLR pro simulaci absenci oboru v rámci nativní výčtu. Není to prokázat úspěšné. Problém je, že to způsobí, že výčty k distribuována do globálního oboru názvů, což vede k obtížné spravovat kolize názvů. V nové syntaxe budeme mít úprava odpovídala u ostatních jazyků CLR v doprovodné oborů v rámci výčtu CLR.  
  
 To znamená, že všechny neúplné použití enumerátor z výčtu CLR nebude rozpoznána pomocí nové syntaxe. Podívejme se na příklad reálného.  
  
```  
// Managed Extensions supporting weak injection  
__gc class XDCMake {  
public:  
   __value enum _recognizerEnum {   
      UNDEFINED,  
      OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6,  
   };  
  
   ListDictionary* optionList;  
   ListDictionary* itagList;  
  
   XDCMake() {  
      optionList = new ListDictionary;  
  
      // here are the problems...  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 Každý ze tří nekvalifikované názvy enumerátor používá (`(1)`, `(2)`, a `(3)`) bude muset být kvalifikovaný v překlad, aby nové syntaxe v pořadí pro zdrojový kód zkompilovat. Tady je správný překlad původního zdrojového kódu:  
  
```  
ref class XDCMake {  
public:  
   enum class _recognizerEnum {  
      UNDEFINED, OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6  
   };  
  
   ListDictionary^ optionList;  
   ListDictionary^ itagList;  
  
   XDCMake() {  
      optionList = gcnew ListDictionary;  
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)  
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)  
      itagList = gcnew ListDictionary;  
      itagList->Add( "returns",   
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)  
   }  
};  
```  
  
 Tato operace změní strategie návrhu mezi nativní a výčtu CLR. S CLR výčtového typu zachování přidruženého oboru v jazyce Visual C++ není nutné ani efektivní zapouzdření deklaraci výčtu v rámci třídy. Tato stylu vyvinuly v době metody cfront 2.0 v rámci zvonku laboratoře také chcete-li vyřešit tento problém znečištění globální název.  
  
 V původní verzi beta nové knihovny iostream podle Jerry Schwarz v zvonku laboratoře Jerry není zapouzdření všechny přidružené výčty definované pro knihovnu a běžné výčty jako `read`, `write`, `append`a tak dále , znemožnila téměř uživatelům zkompilovat svůj existující kód. Jedno řešení by byl do mangle názvy, například `io_read`, `io_write`atd. Druhým řešením by byl změnit jazyk přidáním oboru do výčtu, ale to nebyla to bude možné v době. Střední řešením bylo zapouzdření výčtu v rámci třídy nebo třídy hierarchii, kde název značky i výčty výčtového typu naplnit oboru nadřazených tříd.) Motivace pro umístění alespoň původně výčty v rámci třídy, který je nebyla filozofické, ale praktické odpovědi na problém globální znečištění oboru názvů.  
  
 S Visual C++ výčtu již není jakékoli závažné výhody zapouzdřením výčet v rámci třídy. V faktu, pokud se podíváte `System` obory názvů, zobrazí se tento výčty, třídy a rozhraní obývají stejnému adresnímu prostoru deklarace.  
  
## <a name="see-also"></a>Viz také  
 [Hodnotové typy a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [enum – třída](../windows/enum-class-cpp-component-extensions.md)