---
title: "Sestavení C/C++ izolovaných aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5af0dde80a143166d9824d2739632ca7e7ed4382
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++
Izolované aplikace závisí pouze na souběžně sdílená sestavení a sváže jeho závislé součásti pomocí manifestu. Není nutné pro vaši aplikaci plně izolaci, aby bylo možné správně fungovat v systému Windows. ale investicemi do vytváření aplikace plně izolované, může ušetřit čas Pokud potřebujete služeb vaší aplikace v budoucnu. Další informace o výhodách vytváření plně izolované aplikace najdete v tématu [izolované aplikace](http://msdn.microsoft.com/library/aa375190).  
  
 Při sestavování nativní aplikace C/C++ pomocí Visual C++, generuje systém projektu ve výchozím nastavení sady Visual Studio soubor manifestu, který popisuje závislostí vaší aplikace na knihovny jazyka Visual C++. Pokud jsou jenom závislosti aplikace obsahuje, se pak stane izolované aplikace, jakmile je znovu sestavit pomocí sady Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak budete muset znovu vytvořit tyto knihovny jako souběžně sdílená sestavení kroků popsaných v [sestavení C/C++-souběžného sestavení](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty izolovaných aplikací a souběžně sdílená sestavení](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení C/C++ izolovaných aplikací a souběžně sdílená sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)