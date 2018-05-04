---
title: Sestavení C/C++ izolovaných aplikací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69de94159ef792aedff35efe81e8bb663d571105
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++
Izolované aplikace závisí pouze na souběžně sdílená sestavení a sváže jeho závislé součásti pomocí manifestu. Není nutné pro vaši aplikaci plně izolaci, aby bylo možné správně fungovat v systému Windows. ale investicemi do vytváření aplikace plně izolované, může ušetřit čas Pokud potřebujete služeb vaší aplikace v budoucnu. Další informace o výhodách vytváření plně izolované aplikace najdete v tématu [izolované aplikace](http://msdn.microsoft.com/library/aa375190).  
  
 Při sestavování nativní aplikace C/C++ pomocí Visual C++, generuje systém projektu ve výchozím nastavení sady Visual Studio soubor manifestu, který popisuje závislostí vaší aplikace na knihovny jazyka Visual C++. Pokud jsou jenom závislosti aplikace obsahuje, se pak stane izolované aplikace, jakmile je znovu sestavit pomocí sady Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak budete muset znovu vytvořit tyto knihovny jako souběžně sdílená sestavení kroků popsaných v [sestavení C/C++-souběžného sestavení](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty izolovaných aplikací a souběžně sdílená sestavení](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)