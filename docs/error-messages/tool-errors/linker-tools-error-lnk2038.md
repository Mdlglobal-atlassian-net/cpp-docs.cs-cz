---
title: "Chyba linkerů Lnk2038 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2038
dev_langs: C++
helpviewer_keywords: LNK2038
ms.assetid: b8d0fb35-eee6-4f52-b3c4-239cb4f65656
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 73694359c3fbcaa16455be3ce1197ba99fce56c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2038"></a>Chyba linkerů LNK2038
zjištěna neshoda u '\<název > se: hodnota '\<hodnotu 1 >' Hodnota se neshoduje se\<hodnotu 2 >' v \<filename.obj >  
  
 Byla zjištěna neshoda symbol podle linkeru. Tato chyba znamená, že různých částí aplikace – to zahrnuje knihovny nebo jiný objekt kód, který aplikace odkazuje na – použijte konfliktní definice symbolu. [Zjistit neshoda](../../preprocessor/detect-mismatch.md) – Direktiva pragma se používá k definování takových symbolů a zjistit jejich konfliktní hodnoty.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Této chybě může dojít, když je zastaralý. soubor objektu ve vašem projektu. Než se pokusíte další řešení této chyby, vytvořit nové čisté sestavení zajistit, že objekt soubory jsou aktuální.  
  
-   Visual Studio definuje následující symboly, aby se zabránilo propojení nekompatibilní kód, který může způsobit chyby nebo další neočekávanému chování.  
  
     `_MSC_VER`  
     Určuje počet hlavní verze a podverze – kompilátor Visual C++, který je použit k vytvoření aplikace nebo knihovny. Kód, který je sestaven pomocí jednu verzi Visual C++ compiler není kompatibilní s kód, který je sestaven pomocí na verzi, která má jiný hlavní verze a podverze čísla. Další informace najdete v tématu `_MSC_VER` v [předdefinovaná makra](../../preprocessor/predefined-macros.md).  
  
     Pokud vytváříte odkaz na knihovnu, která není kompatibilní s verzí aplikace Visual C++ compiler, který používáte, a nelze získat nebo sestavení kompatibilní verzi knihovny, můžete použít starší verzi kompilátor k sestavení projektu – stačí změnit **Sada nástrojů platformy** vlastnosti projektu. Další informace najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
     `_ITERATOR_DEBUG_LEVEL`  
     Určuje úroveň zabezpečení a ladění funkcí, které jsou povoleny ve standardní knihovně C++. Tyto funkce můžete změnit reprezentace objektů určité standardní knihovna C++ a tím je provést nekompatibilní s těmi, že použití různých zabezpečení a ladění funkcí. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).  
  
     `RuntimeLibrary`  
     Určuje verzi standardní knihovna C++ a C runtime, který se používá aplikaci nebo knihovny. Kód, který používá jednu verzi modulu runtime standardní knihovna C++ nebo C je nekompatibilní s kódem, který používá jinou verzi. Další informace najdete v tématu [/MD, / MT, /LD (použít běhovou knihovnu)](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
     `_PPLTASKS_WITH_WINRT`  
     Určuje, že kód, který používá [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) je propojená s objekty zkompilovat pomocí různých nastavení [/ZW](../../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru. (**/ZW** podporuje C + +/ CX.) Kód, který používá nebo závisí na knihovně PPL musí být zkompilovány pomocí stejné **/ZW** nastavení, která se používá ve zbývající části aplikace.  
  
     Ujistěte se, že hodnoty tyto symboly jsou konzistentní v rámci projekty v řešení sady Visual Studio a také, zda jsou konzistentní s kódem a knihovny, které vaše aplikace odkazuje na.  
  
## <a name="see-also"></a>Viz také  
 [Chyby a upozornění Linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)