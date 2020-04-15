---
title: Zařazování
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319355"
---
# <a name="marshaling"></a>Zařazování

Technika zařazování COM umožňuje rozhraní vystavená objektem v jednom procesu, které mají být použity v jiném procesu. V zařazování com poskytuje kód (nebo používá kód poskytnutý implementátorrozhraní) jak zabalit parametry metody do formátu, který lze přesunout mezi procesy (stejně jako přes drát na procesy spuštěné na jiných počítačích) a rozbalit tyto parametry na druhém konci. Podobně COM musí provést stejné kroky při návratu z volání.

> [!NOTE]
> Zařazování není obvykle nutné, pokud rozhraní poskytované objektem se používá ve stejném procesu jako objekt. Zařazování však může být potřeba mezi vlákny.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Podrobnosti zařazování](/windows/win32/com/marshaling-details)
