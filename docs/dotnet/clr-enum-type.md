---
title: Typ výčtu CLR | Dokumentace Microsoftu
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
ms.openlocfilehash: a39c451bcff7b5b3b1d7dd9f0d3925616b9d6aab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436221"
---
# <a name="clr-enum-type"></a>Typ enum v prostředí CLR

Deklarace a chování výčty byl změněn z spravovaných rozšíření jazyka C++ na Visual C++.

Deklarace výčtu spravovaných rozšíření předchází `__value` – klíčové slovo. Zde spočívá v k rozlišení nativní výčet z výčtu CLR, který je odvozen z `System::ValueType`, při návrhu obdobné funkce. Příklad:

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Nová syntaxe řeší problém rozlišování nativní a výčtech CLR kdy se klade důraz třídy povaze ten spíše než jeho kořeny typ hodnoty. V důsledku toho `__value` – klíčové slovo se zruší, nahradí dvojici rozložených – klíčové slovo `enum class`. To poskytuje symetrie spárované – klíčové slovo do deklarací odkaz, hodnota a tříd rozhraní:

```
enum class ec;
value class vc;
ref class rc;
interface class ic;
```

Překlad pár výčet `e1` a `e2` Nová syntaxe vypadá takto:

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

Kromě malých syntaktické změnit chování typu výčtu CLR nebylo změněno v několika způsoby:

- Dopředná deklarace výčtu CLR je již nejsou podporovány. Neexistuje žádné mapování. Jednoduše označen jako chyba kompilace.

```
__value enum status; // Managed Extensions: ok
enum class status;   // new syntax: error
```

- Řešení přetížení mezi předdefinované aritmetické typy a `Object` hierarchie tříd má obrácený mezi dvěma jazykové verze. Jako vedlejší efekt se už nebude implicitně převést výčtech CLR pro aritmetické typy.

- V nové syntaxi výčtu CLR udržuje svůj vlastní obor, což není případ spravovaných rozšíření. Dříve byly čítačů viditelné v rámci nadřazeného rozsahu výčtového typu. Nyní čítačů jsou zapouzdřeny v rámci rozsahu výčtového typu.

## <a name="clr-enums-are-a-kind-of-object"></a>Výčtech CLR jsou objekt druh

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

Pro nativní programátor C++ fyzická odpověď na otázku, která instance přetížené `f()` je vyvoláno, je `f(int)`. Výčet je Symbolická konstanta integrální a se podílí na standardní integrální povýšení, které v tomto případě přednost.  A ve skutečnosti v rozšířeních Managed instance, do které překládá volání. Důvodem počet překvapením – ne už při jejich zkušebním na nativní C++ snímek paměti of – ale potřebovali jsme je pro interakci s existující framework BCL (knihovna tříd Base), kde `Enum` je třída nepřímo odvozená z `Object`. V návrhu jazyka Visual C++, instanci `f()` vyvolána je `f(Object^)`.

Způsob, jakým Visual C++ se rozhodl vynutit je tak, aby nepodporoval implicitních převodů mezi typem výčtu CLR a aritmetické typy. To znamená, že jakémukoliv svalování objekt typu výčtu CLR pro aritmetický typ vyžaduje explicitní přetypování. Ano například dány

```
void f( int );
```

jako není přetížená metoda, ve spravovaných rozšíření volání

```
f( rslt ); // ok: Managed Extensions; error: new syntax
```

je ok a hodnota obsažená v rámci `rslt` je implicitně převeden na celočíselnou hodnotu. V jazyce Visual C++ toto volání selže při kompilaci. Chcete-li správně přeložit, jsme musí vložit operátor převodu:

```
f( safe_cast<int>( rslt )); // ok: new syntax
```

## <a name="the-scope-of-the-clr-enum-type"></a>Obor typu výčtu CLR

Jednu z těchto změn mezi jazyky C a C++ se součet rozsahem v rámci struktury zařízení v jazyce C++. V jazyce C je struktura jen data agregovaná bez podpory rozhraní nebo přidružené oboru. To bylo poměrně radikálu změn v době a byla sporné problém pro mnoho nových C++ uživatelů pocházející z jazyka C. Vztah mezi nativním a výčtu CLR je obdobou.

Ve spravovaných rozšíření byl proveden pokus o definování slabě vloženého názvy čítačů z výčtu CLR k simulaci neexistence rozsahem v rámci nativní výčet. Není to prokázat úspěšné. Problém je, že to způsobí, že čítačů pro uložená v globálním oboru názvů, což vede k obtížné spravovat kolize názvů. V nové syntaxi můžeme mít potvrzeny do jiných jazyků CLR při podpoře oborů v rámci výčtu CLR.

To znamená, že všechny nekvalifikované pomocí čítače výčtu CLR nebude rozpoznána pomocí nové syntaxe. Pojďme se podívat na příklad reálného světa.

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

Všechny nekvalifikované tři použití názvům výčtů (`(1)`, `(2)`, a `(3)`) bude muset být kvalifikovaný v překladu novou syntaxi, aby se zdrojový kód pro kompilaci. Tady je správný překlad původního zdrojového kódu:

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

Tím se změní návrhu strategie mezi nativní a výčtu CLR. Pomocí výčtu CLR zachování přidružené obor v jazyce Visual C++ není nezbytné ani efektivní k zapouzdření deklarace výčtu v rámci třídy. Tohoto idiomu vyvinula v době výskytu cfront 2.0 v rámci zvonku laboratoře také za účelem řešení problému znečištění globální název.

V původní verzi beta nová Knihovna iostream – podle Jerry Schwarz v laboratořích zvonku Jerry není zapouzdření všechny přidružené výčty definované pro knihovnu a běžných čítačů, jako `read`, `write`, `append`, a tak dále , provedli pro uživatele pro kompilaci svůj existující kód téměř nemožné. Jedním řešením by byla mangle názvy, například `io_read`, `io_write`atd. Druhým řešením by byl změnit jazyk tak, že přidáte obor na výčet, ale to není možné době. Střední řešení bylo zapouzdření výčtu v rámci třídy nebo třídy hierarchie, kde název značky i čítače výčtu vyplnit nadřazený rozsah třídy.) To znamená, motivace pro umístění v rámci třídy, výčty alespoň původně nebyl filozofické, ale je praktické reakci na problém globální znečištění oboru názvů.

Pomocí výčtu jazyka Visual C++ již není jakékoli závažné výhody zapouzdření výčtu v rámci třídy. Ve skutečnosti, pokud se podíváte `System` obory názvů, zobrazí se tento výčty, třídy a rozhraní obývají stejné místo prohlášení.

## <a name="see-also"></a>Viz také

[Hodnotové typy a jejich chování (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Třída výčtu](../windows/enum-class-cpp-component-extensions.md)