---
title: EXPORTY | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c642a623e76a9e1344a90efd4f0a47ad195c553e
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322186"
---
# <a name="exports"></a>EXPORTY

Představuje oddíl jednu nebo víc definic exportu určujících exportovaným názvům nebo řadové číslovky funkce nebo data. Každá definice musí být na samostatném řádku.  
  
```DEF  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>Poznámky  

První *definice* může být na stejném řádku jako `EXPORTS` – klíčové slovo nebo na následujícím řádku. Na. Soubor DEF mohou obsahovat jednu nebo více `EXPORTS` příkazy.  
  
Syntaxe pro export *definice* je:  
  
```DEF
entryname[=internal_name|other_module.another_exported_name] [@Ordinal [NONAME]] [[PRIVATE] | [DATA]]
```

*název_položky* je název funkce nebo proměnná, která chcete exportovat. Toto je povinné. Pokud se název, který exportujete liší od názvu v knihovně DLL, zadejte název pro export v knihovně DLL pomocí *internal_name*. Například, pokud vaše knihovna DLL exportuje funkce `func1` a chcete, aby volající použít ho jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=func1
```

Pokud se název, který můžete exportovat z jiných modulu, zadejte název pro export v knihovně DLL pomocí *other_module.exported_name*. Například, pokud vaše knihovna DLL exportuje funkce `other_module.func1` a chcete, aby volající použít ho jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=other_module.func1
```

Protože kompilátor Visual C++ používá dekorování názvů pro funkce jazyka C++, musíte použít upravený název internal_name nebo definovat exportované funkce tak, že používání příkazu extern "C" ve zdrojovém kódu. Kompilátor také upraví funkcí jazyka C, které používají [__stdcall](../../cpp/stdcall.md) konvence s předponou podtržítka (_) a příponu skládá z volání zavináč (@) následovaným počtem bajtů (v desítkové soustavě) v seznamu argumentů.  
  
Pokud chcete zjistit dekorované názvy produkované kompilátorem, použijte [DUMPBIN](../../build/reference/dumpbin-reference.md) nástroje nebo linker [/MAP](../../build/reference/map-generate-mapfile.md) možnost. Dekorované názvy jsou specifické pro kompilátor. Pokud exportujete dekorované názvy ve. Soubor DEF spustitelné soubory, které na knihovnu DLL musí být sestaveny také pomocí stejné verze kompilátoru. Tím se zajistí, že dekorované názvy volajícího odpovídaly exportovaným názvům v. Soubor DEF.  
  
Můžete použít*ordinální* k určení, že číslo a ne název funkce, půjdou do tabulky exportu knihovny DLL. Mnoho knihoven DLL Windows exportovat řadové číslovky důvodu podpory původního kódu. Bylo běžné použití řadové číslovky v 16bitového kódu Windows, protože může pomoct minimalizovat velikost knihovny DLL. Nedoporučujeme export funkcí podle pořadových čísel, pokud ho vaše knihovna DLL klienti potřebovat pro stále podporuje starší verze. Vzhledem k tomu,. LIB soubor bude obsahovat mapování mezi řadová číslovka a funkci, můžete použít název funkce, jako byste normálně v projektech, které používají knihovnu DLL.  
  
Pomocí volitelného `NONAME` – klíčové slovo, můžete exportovat na základě pořadí pouze a snížit velikost tabulky exportu v výslednou knihovnu DLL. Nicméně pokud chcete použít [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) na knihovnu DLL, musíte znát řadová číslovka, protože nebude platný název.  
  
Optional – klíčové slovo `PRIVATE` brání *Název_položky* nebudou zahrnuty do knihovna importů generovaná odkaz. Export obrázku také generovány podle propojení nemá vliv.  
  
Optional – klíčové slovo `DATA` Určuje, že export dat, není kód. Tento příklad ukazuje, jak jste mohli exportovat data proměnnou s názvem `exported_global`:  
  
```DEF  
EXPORTS  
   exported_global DATA  
```  
  
Existují čtyři způsoby, jak exportovat definici uvedené v doporučené pořadí:  
  
1.  [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu  
  
2.  `EXPORTS` Výroky. Soubor DEF  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu LINK  
  
4.  A [komentář](../../preprocessor/comment-c-cpp.md) směrnice ve zdrojovém kódu formuláře `#pragma comment(linker, "/export: definition ")`  
  
Všechny čtyři metody je možné ve stejném programu. Při propojení buildů program, který obsahuje exporty, také vytvoří knihovnu importu, není-li. EXP soubor se používá v sestavení.  
  
Tady je příklad oddílu EXPORTŮ:  
  
```DEF  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
Při exportu proměnné z knihovny DLL pomocí. Soubor DEF, není nutné zadat `__declspec(dllexport)` na proměnnou. Ale v žádném souboru, který používá knihovnu DLL, musí stále používáte `__declspec(dllimport)` u deklarace data.  
  
## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)
