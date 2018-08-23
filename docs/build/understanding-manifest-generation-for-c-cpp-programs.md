---
title: Principy generování manifestu pro programy C/C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40dbc61009cdfaa5621335cfb78dd10eae2138ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465395"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Základní informace o generování manifestu pro programy C/C++
A [manifest](http://msdn.microsoft.com/library/aa375365) je dokument XML, který může být externí soubor XML nebo prostředek vložena do aplikace nebo sestavení. Manifest [izolované aplikace](http://msdn.microsoft.com/library/aa375190) slouží ke správě názvů a verzí sdílená sestavení vedle sebe, pro které aplikace by měla vytvořit vazbu za běhu. Manifest sestavení vedle sebe určuje závislých na názvy, verze, prostředky a jiná sestavení.  
  
 Existují dva způsoby vytvoření manifestu izolované aplikace nebo sestavení vedle sebe. Nejprve Autor sestavení můžete ručně vytvořit soubor manifestu následující pravidla a požadavkům na názvy. Případně pokud program pouze závisí na sestavení Visual C++, jako je například CRT, MFC, ATL nebo jiné, pak manifestu mohou být generovány automaticky linkeru.  
  
 Hlavičky knihoven Visual C++ obsahují informace o sestavení, a když tyto knihovny jsou zahrnuty v kódu aplikace, tyto informace sestavení používá propojovací program k vytvoření manifestu pro koncovém binárním souboru. Propojovací program nelze vložit soubor manifestu do binárního souboru a můžou jenom generovat manifest jako externího souboru. Ve všech případech nemusí fungovat s manifestu jako externího souboru. Například se doporučuje, aby soukromých sestavení mají vložených manifestů. V sestaveních příkazového řádku jako jsou ty, které používají nmake sestavovat kód lze jej vkládat manifestu pomocí nástroje manifestu; Další informace najdete v části [generování manifestu v příkazovém řádku](../build/manifest-generation-at-the-command-line.md). Při sestavování v sadě Visual Studio, může být manifestu vložen nastavením vlastnosti pro nástroj manifest v **vlastnosti projektu** dialogové okno; viz [generování manifestu v sadě Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncept izolovaných aplikací a sestavení vedle sebe](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)