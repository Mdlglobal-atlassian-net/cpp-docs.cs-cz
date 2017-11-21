---
title: "Principy generování manifestu pro programy C/C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b0d17ba04dc1648d9aa05dff98715ef9a80a230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Základní informace o generování manifestu pro programy C/C++
A [manifest](http://msdn.microsoft.com/library/aa375365) je dokument XML, který může být externí soubor XML nebo prostředek vložena do aplikace nebo sestavení. Manifest [izolované aplikace](http://msdn.microsoft.com/library/aa375190) slouží ke správě názvy a verze sdílené souběžně sdílená sestavení, na které aplikace by měla vytvořit vazbu v době běhu. Manifest souběžně sdílená sestavení určuje jeho závislé součásti na názvy, verze, prostředky a jiné sestavení.  
  
 Existují dva způsoby vytvoření manifestu pro izolované aplikace nebo souběžně sdílená sestavení. Nejprve autora sestavení můžete ručně vytvořit soubor manifestu následující pravidla a pojmenování požadavky. Případně pokud program závisí na tom, Visual C++ sestavení například CRT, MFC, ATL nebo jiné, pak manifestu může být generována automaticky linkeru.  
  
 Hlavičky knihoven Visual C++ obsahovat informace o sestavení a když knihovny jsou zahrnuty v kódu aplikace, je k vytvoření manifestu pro konečné binární linkeru používá tyto informace sestavení. Linkeru nevloží souboru manifestu uvnitř binárního souboru a můžete pouze generování manifestu jako externí soubor. S jako externí soubor manifestu, nemusí fungovat pro všechny scénáře. Například se doporučuje, aby soukromá sestavení vložených manifesty. V sestavení příkazového řádku jako jsou ty, které nmake použít k vytvoření kódu lze jej vkládat manifestu pomocí nástroje manifestu; Další informace najdete v části [generování manifestu v příkazovém řádku](../build/manifest-generation-at-the-command-line.md). Při sestavování v [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], lze jej vkládat manifestu nastavením vlastnosti pro nástroj manifestu v **vlastnosti projektu** dialogové okno; viz [generování manifestu v sadě Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty izolovaných aplikací a souběžně sdílená sestavení](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení C/C++ izolovaných aplikací a souběžně sdílená sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)