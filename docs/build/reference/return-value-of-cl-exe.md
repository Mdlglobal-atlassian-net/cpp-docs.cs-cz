---
title: "Návratová hodnota cl.exe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85ca64178a4914cfbbc8b3a717b87ab5590cd778
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="return-value-of-clexe"></a>Návratová hodnota cl.exe
Program cl.exe vrátí při úspěchu nulovou hodnotu (bez chyb), v opačném případě nenulovou hodnotu  
  
 Vrácená hodnota programu cl.exe může být užitečná při kompilaci ze skriptu, prostředí powershell, souboru .cmd nebo .bat. Pro případ, že se vyskytnou chyby nebo upozornění, doporučujeme výstup kompilátoru zachytit, abyste je mohli vyřešit.  
  
 Program cl.exe má příliš mnoho možných ukončovacích kódů, než aby zde byly všechny uvedeny. Můžete vyhledat kód chyby v winerror.h nebo ntstatus.h soubory zahrnuty v systému Windows Software Development Kit v % ProgramFiles (x86) %\Windows sadách\\`version`\Include\shared\ adresáře. Kvůli vyhledávání se kódy chyb vrácené v desítkové soustavě musí převést do šestnáctkové soustavy. Například kód chyby -1073741620 se do šestnáctkové soustavy převede jako 0xC00000CC. Tato chyba se nachází v souboru ntstatus.h s odpovídající zprávou „Zadaný sdílený název nelze najít na vzdáleném serveru“. Zaváděná seznam kódy chyb systému Windows, naleznete v části [&#91; MS-ERREF &#93;: kódy chyb Windows](http://msdn.microsoft.com/library/cc231196).  
  
 Ke zjištění významu chybových zpráv kompilátoru můžete použít také nástroj pro vyhledávání chyb v sadě Visual Studio. V příkazovém prostředí sady Visual Studio, zadejte **errlook.exe** spustit nástroj; nebo v prostředí Visual Studio IDE v řádku nabídek zvolte **nástroje**, **Chyba vyhledávání**. Zadáním chybové hodnoty najdete popisný text přidružený k této chybě. Další informace najdete v části [errlook – odkaz](../../build/reference/errlook-reference.md).  
  
## <a name="remarks"></a>Poznámky  
 Následuje ukázkový soubor .bat, který používá vrácenou hodnotu programu cl.exe.  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## <a name="see-also"></a>Viz také  
 [Syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md)