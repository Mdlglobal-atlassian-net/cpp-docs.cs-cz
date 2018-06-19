---
title: EXPORTUJE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7cc7a9995fdc5be786712752e30015337b9f1607
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376823"
---
# <a name="exports"></a>EXPORTY
Představuje oddíl jeden nebo více export definice, které zadáte exportovaný názvy nebo řadové číslovky funkce nebo data. Každý definice musí být na samostatném řádku.  
  
```  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>Poznámky  
 První `definition` může být na stejném řádku, jako `EXPORTS` – klíčové slovo nebo na následujícím řádku. Na. DEF soubor může obsahovat jednu nebo více `EXPORTS` příkazy.  
  
 Syntaxe o export `definition` je:  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` je název funkce nebo proměnná, která chcete exportovat. To je potřeba. Pokud název, který chcete exportovat se liší od názvu v knihovně DLL, zadejte název s exportem v knihovně DLL pomocí `internalname`. Například, pokud vaše knihovna DLL export funkce `func1` a chcete, aby volající pro použití jako `func2`, zadali byste:  
  
```  
EXPORTS  
   func2=func1  
```  
  
 Protože Visual C++ compiler používá dekorování názvů pro funkcí jazyka C++, je nutné použít upravený název jako `entryname` nebo `internalname`, nebo definujte exportovaných funkcí s použitím `extern "C"` ve zdrojovém kódu. Kompilátor také upraví funkcí jazyka C, které používají [__stdcall](../../cpp/stdcall.md) konvence s předponu podtržítka (_) a příponu skládá z volání znaku zavináče (@) následovaný počtem bajtů (decimální): v seznamu argumentů.  
  
 Dekorované názvy produkované kompilátorem najdete použít [DUMPBIN](../../build/reference/dumpbin-reference.md) nástroje nebo linkeru [/MAP](../../build/reference/map-generate-mapfile.md) možnost. Dekorované názvy jsou specifické pro kompilátoru. Pokud exportujete dekorované názvy v. DEF souboru, spustitelné soubory, které na knihovnu DLL musí také být vytvořené použít stejná verze kompilátoru. To zajistí, že dekorované názvy v volající odpovídají exportovaný názvy v. DEF soubor.  
  
 Můžete použít`ordinal` k určení, že číslo a nikoli na název funkce přejde do tabulky export knihovny DLL. Mnoho knihovny DLL systému Windows exportovat řadové číslovky k podpoře starší verze kódu. Bylo běžné použití řadové číslovky v 16bitové kód systému Windows, protože může pomoci minimalizovat velikost knihovny DLL. Nedoporučujeme export funkcí podle pořadí, pokud vaše knihovna DLL klienti ho potřebovat pro podporuje starší verze. Protože. LIB soubor bude obsahovat mapování mezi řadová číslovka a funkce, můžete použít název funkce jako za normálních okolností byste v projektech, které používají knihovnu DLL.  
  
 Pomocí volitelného `NONAME` – klíčové slovo, můžete exportovat podle pořadových pouze a zmenšit velikost tabulky export výsledného knihovny DLL. Ale pokud budete chtít použít [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) na knihovnu DLL, musíte znát řadová číslovka, protože název nebude platný.  
  
 Optional – klíčové slovo `PRIVATE` brání `entryname` z nebudou zahrnuty do knihovny importu generované odkaz. Export v bitové kopii také vygenerované propojení nemá vliv.  
  
 Optional – klíčové slovo `DATA` Určuje, že je exportu dat, nikoli kódu. Tento příklad ukazuje, jak může exportovat data proměnné s názvem `exported_global`:  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 Existují čtyři způsoby, jak exportovat definici uvedené v doporučené pořadí:  
  
1.  [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu  
  
2.  `EXPORTS` Příkaz v. Soubor DEF  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu odkaz  
  
4.  A [komentář](../../preprocessor/comment-c-cpp.md) direktivy ve zdrojovém kódu ve tvaru `#pragma comment(linker, "/export: definition ")`  
  
 Všechny čtyři metody lze použít ve stejný program. Při propojení sestavení program, který obsahuje exportuje, také vytvoří knihovnu importu, pokud. EXP soubor se používá v buildu.  
  
 Tady je příklad oddílu export:  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 Při exportu proměnné z knihovny DLL pomocí. DEF souboru, není nutné zadat `__declspec(dllexport)` na proměnnou. Však ve všech souborů, které používá knihovnu DLL, musíte pořád použít `__declspec(dllimport)` na deklaraci data.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)