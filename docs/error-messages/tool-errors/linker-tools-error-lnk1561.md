---
title: "Chyba linkerů Lnk1561 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1561
dev_langs: C++
helpviewer_keywords: LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3a6ad889969292a65afb7b363412eaf7d7a6430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1561"></a>Chyba linkerů LNK1561
vstupní bod musí být definován.  
  
Nebyl nalezen linkeru *vstupní bod*, počáteční funkce k volání v vaší spustitelný soubor. Ve výchozím nastavení, hledá linkeru `main` nebo `wmain` funkce pro konzolovou aplikaci `WinMain` nebo `wWinMain` funkce pro aplikace pro Windows, nebo `DllMain` pro knihovnu DLL, kterou vyžaduje inicializace. Můžete zadat další funkce pomocí [/Entry](../../build/reference/entry-entry-point-symbol.md) – možnost linkeru.  
  
Tato chyba může mít několik příčin:  
-   Nesmí mít zahrnuté soubor, který definuje vstupní bod v seznamu souborů propojení. Ověřte, že je propojený soubor, který obsahuje funkce vstupního bodu do vaší aplikace.  
-   Jste definovali vstupního bodu pomocí funkce nesprávný podpis; Například můžete pravděpodobně zadáno chybně nebo název funkce použit nesprávný případu nebo nesprávně zadán návratový typ nebo typy parametrů.  
-   Zadali jste [/dll](../../build/reference/dll-build-a-dll.md) možnost při vytváření knihovny DLL.  
-   Možná jste zadali název funkce vstupního bodu správně po použití [/Entry](../../build/reference/entry-entry-point-symbol.md) – možnost linkeru.  
-   Pokud používáte [LIB](../../build/reference/lib-reference.md) nástroj k vytváření knihovny DLL, jste zadali .def souboru. Pokud ano, odstraňte soubor .def z sestavení.    
  
Při vytváření aplikace, hledá linkeru funkci vstupního bodu volat spuštění kódu. Toto je funkce, která je volána po načtení aplikace a modul runtime je inicializován. Je nutné zadat funkci vstupního bodu pro aplikaci nebo aplikaci nelze spustit. Vstupní bod je volitelný pro knihovnu DLL. Ve výchozím nastavení, linkeru hledá funkce vstupního bodu, který obsahuje jedno z několika konkrétní názvy a podpisy, jako například `int main(int, char**)`. Můžete zadat jiný název funkce jako položka bodu pomocí možnosti linkeru/Entry.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```