---
title: Sestavení izolovaných aplikací C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 42192ad9388a8e69b70947c20c6fa7ee428a2bb9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220969"
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++

Izolované aplikace závisí jenom na sestavení vedle sebe a sváže s jeho závislosti pomocí manifestu. Není nutné pro vaši aplikaci, která bude plně oddělené, aby bylo možné správně spustit na Windows; ale Investujete do vytváření aplikace plně izolované, může ušetřit čas potřebujete služby vaší aplikace v budoucnu. Další informace o výhodách vytváření plně izolované aplikace najdete v tématu [izolované aplikace](/windows/desktop/SbsCs/isolated-applications).

Při vytváření nativní C /C++ aplikace pomocí sady Visual Studio, ve výchozím nastavení systém projektu sady Visual Studio generuje soubor manifestu, který popisuje závislosti vašich aplikací v knihovnách sady Visual Studio. Pokud se jedná jenom závislosti aplikace obsahuje, se pak stane izolované aplikace poté, co je znovu sestavit pomocí sady Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak je nutné znovu sestavit těchto knihoven jako sestavení vedle sebe kroků popsaných v [vytváření sestavení C/C++-souběžně](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
