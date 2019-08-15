---
title: Zařazování
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492043"
---
# <a name="marshaling"></a>Zařazování

Technika modelu COM pro zařazování umožňuje rozhraní vystavené objektem v jednom procesu pro použití v jiném procesu. V zařazování poskytuje model COM kód (nebo používá kód poskytnutý implementací rozhraní) k zabalení parametrů metody do formátu, který lze přesunout mezi procesy (stejně jako, napříč vodiči a procesy běžícími na jiných počítačích) a rozbalením těchto parametrů. na druhém konci. Podobně musí model COM provést stejné kroky při návratu z volání.

> [!NOTE]
>  Zařazování není obvykle nutné, pokud je rozhraní poskytované objektem používáno ve stejném procesu jako objekt. Zařazování ale může být potřeba mezi vlákny.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Podrobnosti zařazování](/windows/win32/com/marshaling-details)
