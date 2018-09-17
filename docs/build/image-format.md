---
title: Formát obrázku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715413"
---
# <a name="image-format"></a>Formát obrázku

Formát spustitelná image, která je typu PE32 +. Spustitelné bitové kopie (knihovny DLL a exe) jsou omezena na maximální velikosti 2 GB, takže relativní adresy s 32bitovým posunem můžete používat k adresování statických dat bitové kopie. Tato data zahrnují tabulky importních adres, řetězcové konstanty, statické globálních dat a tak dále.

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)