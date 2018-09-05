---
title: Zařazování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f9e8e080837ed109a786c2123ab90624d994cd1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753724"
---
# <a name="marshaling"></a>zařazování

Metoda COM zařazování umožňuje vystavených objektem v jednom procesu, který se má použít v jiném procesu. Zařazování, COM poskytuje kód (nebo názvu souboru používá kód poskytované rozhraní implementátor) se zabalit parametry metody do formátu, který je možné přesunout napříč procesy (a sítí pro procesy spuštěné na jiných počítačích) a rozbalte tyto parametry na druhém konci. COM, musí provést stejné kroky při návratu z volání.

> [!NOTE]
>  Zařazování není obvykle nutné při rozhraní zadané v objektu se používá ve stejném procesu jako objekt. Zařazování však může být potřeba mezi vlákny.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)   
[Podrobnosti o zařazování](/windows/desktop/com/marshaling-details)

