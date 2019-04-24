---
title: zařazování
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262382"
---
# <a name="marshaling"></a>zařazování

Metoda COM zařazování umožňuje vystavených objektem v jednom procesu, který se má použít v jiném procesu. Zařazování, COM poskytuje kód (nebo názvu souboru používá kód poskytované rozhraní implementátor) se zabalit parametry metody do formátu, který je možné přesunout napříč procesy (a sítí pro procesy spuštěné na jiných počítačích) a rozbalte tyto parametry na druhém konci. COM, musí provést stejné kroky při návratu z volání.

> [!NOTE]
>  Zařazování není obvykle nutné při rozhraní zadané v objektu se používá ve stejném procesu jako objekt. Zařazování však může být potřeba mezi vlákny.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Podrobnosti o zařazování](/windows/desktop/com/marshaling-details)
