---
title: Sestavení izolovaných aplikací C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: e02fec4115d328dd8230d68ddb65b380ec743dc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274704"
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++

Izolované aplikace závisí jenom na sestavení vedle sebe a sváže s jeho závislosti pomocí manifestu. Není nutné pro vaši aplikaci, která bude plně oddělené, aby bylo možné správně spustit na Windows; ale Investujete do vytváření aplikace plně izolované, může ušetřit čas potřebujete služby vaší aplikace v budoucnu. Další informace o výhodách vytváření plně izolované aplikace najdete v tématu [izolované aplikace](/windows/desktop/SbsCs/isolated-applications).

Při vytváření nativní aplikace C/C++ pomocí jazyka Visual C++, generuje systém projektu ve výchozím nastavení sady Visual Studio soubor manifestu, který popisuje závislostí vaší aplikace na knihovny Visual C++. Pokud se jedná jenom závislosti aplikace obsahuje, se pak stane izolované aplikace poté, co je znovu sestavit pomocí sady Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak je nutné znovu sestavit těchto knihoven jako sestavení vedle sebe kroků popsaných v [vytváření sestavení C/C++-souběžně](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
