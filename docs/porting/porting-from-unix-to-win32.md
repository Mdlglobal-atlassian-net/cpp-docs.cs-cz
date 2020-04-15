---
title: Spouštění programů pro Linux ve Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: c91bcf1c9384cd71811d42a14b98dc155626a4d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368471"
---
# <a name="running-linux-programs-on-windows"></a>Spouštění programů pro Linux ve Windows

Chcete-li spustit program Linux v systému Windows, máte tyto možnosti:

- Spusťte program tak, jak je v podsystému Windows pro Linux (WSL). Ve WSL se program spouští přímo na hardwaru počítače, nikoli ve virtuálním počítači. WSL také umožňuje přímé volání souborového systému mezi systémy Windows a Linux, což odstraňuje potřebu přenosu SSL. WSL je navržen jako prostředí příkazového řádku a nedoporučuje se pro aplikace náročné na grafiku. Další informace naleznete v tématu [Windows Subsystem for Linux Documentation](/windows/wsl/about).
- Spusťte program tak, jak je v linuxovém virtuálním počítači nebo kontejneru Dockeru, buď na místním počítači, nebo v Azure. Další informace najdete v tématu [Virtuální počítače](https://azure.microsoft.com/services/virtual-machines/) a Docker [v Azure](https://docs.microsoft.com/azure/docker/).
- Kompilujte program pomocí gcc nebo clang v prostředí [MinGW](http://MinGW.org/) nebo [MinGW-w64,](https://sourceforge.net/p/mingw-w64/wiki2/Home/) které poskytují překladvrstvu z Linuxu do systémových volání Windows.
- Kompilujte a spusťte program pomocí gcc nebo clang v prostředí [Cygwin,](https://www.cygwin.com/) který poskytuje úplnější linuxové prostředí v systému Windows ve srovnání s MinGW nebo MinGW-w64.
- Ručně přenést kód z Linuxu a kompilovat pro Windows pomocí Microsoft C++ (MSVC). To zahrnuje refaktoring kódu nezávislého na platformě do samostatných knihoven a pak re-psaní kódu specifického pro Linux pro použití kódu specifického pro Systém Windows (například Win32 nebo DirectX ROZHRANÍ API). Pro aplikace, které vyžadují vysoce výkonnou grafiku, je to pravděpodobně nejlepší volba.
