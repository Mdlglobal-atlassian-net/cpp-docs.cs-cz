---
title: Sestavení izolovaných aplikací C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493346"
---
# <a name="building-cc-isolated-applications"></a>Sestavení izolovaných aplikací C/C++

Izolovaná aplikace závisí pouze na souběžných sestaveních a váže se k jejím závislostem pomocí manifestu. Není nutné, aby vaše aplikace byla plně izolovaná, aby fungovala správně v systému Windows. díky investicím do plné izolace vaší aplikace ale můžete ušetřit čas, pokud budete v budoucnu potřebovat svou aplikaci obsluhovat. Další informace o výhodách plné izolace vaší aplikace najdete v tématu [izolované aplikace](/windows/win32/SbsCs/isolated-applications).

Při sestavování nativní C/C++ aplikace pomocí sady Visual Studio ve výchozím nastavení vygeneruje projektový systém sady Visual Studio soubor manifestu, který popisuje závislosti vaší aplikace v knihovnách sady Visual Studio. Pokud se jedná o jediné závislosti, které vaše aplikace má, pak se tato aplikace stal izolovanou aplikací, jakmile bude znovu sestavena se sadou Visual Studio. Pokud vaše aplikace používá jiné knihovny za běhu, pak možná budete muset tyto knihovny znovu sestavit jako souběžná sestavení podle kroků popsaných v tématu sestavení [CC++ /souběžného sestavení](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
