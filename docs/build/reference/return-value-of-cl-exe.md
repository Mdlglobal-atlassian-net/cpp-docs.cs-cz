---
title: Návratová hodnota cl.exe | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3925044f8cf827c38610308226cd6c32008a59a1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206093"
---
# <a name="return-value-of-clexe"></a>Návratová hodnota cl.exe
Program cl.exe vrátí při úspěchu nulovou hodnotu (bez chyb), v opačném případě nenulovou hodnotu  
  
 Vrácená hodnota programu cl.exe může být užitečná při kompilaci ze skriptu, prostředí powershell, souboru .cmd nebo .bat. Pro případ, že se vyskytnou chyby nebo upozornění, doporučujeme výstup kompilátoru zachytit, abyste je mohli vyřešit.  
  
 Program cl.exe má příliš mnoho možných ukončovacích kódů, než aby zde byly všechny uvedeny. Můžete vyhledat kód chyby ve winerror.h nebo ntstatus.h soubory součástí sady Windows Software Development Kit ve složce % ProgramFiles (x86) %\Windows sady\\`version`\Include\shared\ adresáře. Kvůli vyhledávání se kódy chyb vrácené v desítkové soustavě musí převést do šestnáctkové soustavy. Například kód chyby -1073741620 se do šestnáctkové soustavy převede jako 0xC00000CC. Tato chyba se nachází v souboru ntstatus.h s odpovídající zprávou „Zadaný sdílený název nelze najít na vzdáleném serveru“. Ke stažení seznam kódů chyb Windows najdete v tématu [ &#91;MS-ERREF&#93;: kódy chyb Windows](https://msdn.microsoft.com/library/cc231196).  
  
 Ke zjištění významu chybových zpráv kompilátoru můžete použít také nástroj pro vyhledávání chyb v sadě Visual Studio. V příkazovém prostředí sady Visual Studio, zadejte **errlook.exe** spustit nástroj; nebo v sadě Visual Studio IDE, v řádku nabídek zvolte **nástroje**, **vyhledávání chyby**. Zadáním chybové hodnoty najdete popisný text přidružený k této chybě. Další informace najdete v části [errlook – odkaz](../../build/reference/errlook-reference.md).  
  
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