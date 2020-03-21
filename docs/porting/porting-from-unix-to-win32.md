---
title: Spouštění programů pro Linux ve Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 1c1807cee07db479a91f45e21434b3ba13be2ab6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076891"
---
# <a name="running-linux-programs-on-windows"></a>Spouštění programů pro Linux ve Windows

Chcete-li spustit program Linux v systému Windows, máte tyto možnosti:

- Spusťte program tak, jak je v subsystému Windows pro Linux (WSL). V WSL se program provádí přímo na hardwaru počítače, nikoli na virtuálním počítači. WSL také umožňuje přímé volání systému souborů mezi systémy Windows a Linux a odstraňuje nutnost přenosu SSL. WSL je navržen jako prostředí příkazového řádku a nedoporučuje se pro aplikace náročné na grafiku. Další informace najdete v [dokumentaci k subsystému Windows pro Linux](/windows/wsl/about).
- Spusťte program tak, jak je ve virtuálním počítači se systémem Linux nebo kontejneru Docker, a to buď v místním počítači, nebo v Azure. Další informace najdete v tématu [Virtual Machines](https://azure.microsoft.com/services/virtual-machines/) a [Docker v Azure](https://docs.microsoft.com/azure/docker/).
- Zkompilujte program pomocí RSZ nebo Clang v prostředích [MINGW](http://MinGW.org/) nebo [MINGW-W64](https://MinGW-w64.org/doku.php) , která poskytují vrstvu překladu ze systému Linux na volání systému Windows.
- Zkompilujte a spusťte program pomocí RSZ nebo Clang v prostředí [Cygwin](https://www.cygwin.com/) , které ve srovnání s MinGW nebo MINGW-W64 nabízí ucelené prostředí Linux ve Windows.
- Ruční portujte svůj kód z Linux a zkompilujte pro Windows pomocí C++ Microsoft (MSVC). To zahrnuje refaktoring kódu nezávislého na platformě do samostatných knihoven a následném přepsání kódu specifického pro Linux pro použití kódu specifického pro systém Windows (například Win32 nebo rozhraní DirectX API). Pro aplikace, které vyžadují grafiku s vysokým výkonem, se pravděpodobně jedná o nejlepší možnost.
