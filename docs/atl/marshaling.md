---
title: zařazování
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: a6129ba96cf3ac11339a8ab953e0838127f8fb3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569790"
---
# <a name="marshaling"></a>zařazování

Metoda COM zařazování umožňuje vystavených objektem v jednom procesu, který se má použít v jiném procesu. Zařazování, COM poskytuje kód (nebo názvu souboru používá kód poskytované rozhraní implementátor) se zabalit parametry metody do formátu, který je možné přesunout napříč procesy (a sítí pro procesy spuštěné na jiných počítačích) a rozbalte tyto parametry na druhém konci. COM, musí provést stejné kroky při návratu z volání.

> [!NOTE]
>  Zařazování není obvykle nutné při rozhraní zadané v objektu se používá ve stejném procesu jako objekt. Zařazování však může být potřeba mezi vlákny.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Podrobnosti o zařazování](/windows/desktop/com/marshaling-details)

