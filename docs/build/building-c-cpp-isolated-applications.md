---
title: Sestavení izolovaných aplikací C/C++ | Dokumentace Microsoftu
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
ms.openlocfilehash: 26a21eb12d9da1caaae3dbd12fe2f3ffd1194bac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219090"
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++
Izolované aplikace závisí jenom na sestavení vedle sebe a sváže s jeho závislosti pomocí manifestu. Není nutné pro vaši aplikaci, která bude plně oddělené, aby bylo možné správně spustit na Windows; ale Investujete do vytváření aplikace plně izolované, může ušetřit čas potřebujete služby vaší aplikace v budoucnu. Další informace o výhodách vytváření plně izolované aplikace najdete v tématu [izolované aplikace](/windows/desktop/SbsCs/isolated-applications).  
  
 Při vytváření nativní aplikace C/C++ pomocí jazyka Visual C++, generuje systém projektu ve výchozím nastavení sady Visual Studio soubor manifestu, který popisuje závislostí vaší aplikace na knihovny Visual C++. Pokud se jedná jenom závislosti aplikace obsahuje, se pak stane izolované aplikace poté, co je znovu sestavit pomocí sady Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak je nutné znovu sestavit těchto knihoven jako sestavení vedle sebe kroků popsaných v [vytváření sestavení C/C++-souběžně](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncept izolovaných aplikací a sestavení vedle sebe](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)