---
title: Spuštění aplikace C++ - clr v předchozí verzi modulu Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
ms.openlocfilehash: 9b26439d389cb4035541cedde8a5b5cf50682098
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786931"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Spuštění aplikace C++ /clr v předchozí verzi modulu runtime

Pokud není uvedeno jinak, aplikace v jazyce C++ rozhraní .NET Framework je určený pro spouštět verze společného běhového jazykového (CLR), kterou kompilátor používá k sestavení aplikace. Je však možné, aplikace .exe, pro kterou je vytvořena jedna verze modulu runtime pro spuštění na jakoukoli jinou verzi, která poskytuje požadovanou funkci.

Chcete-li to provést, zadejte soubor app.config, který obsahuje informace o verzi modulu runtime v `supportedRuntime` značky.

V době běhu souboru app.config musí mít název ve tvaru *název_souboru.přípona*.config, kde *název_souboru.přípona* je název spustitelného souboru, který spouští aplikaci, a musí být ve stejném adresáři jako spustitelný soubor. Například pokud vaše aplikace jmenuje TestApp.exe, soubor app.config by měl jmenovat TestApp.exe.config.

Pokud zadáte více než jedna verze modulu runtime a aplikace bude spuštěna na počítači, který má více než jedna verze modulu runtime nainstalovaný, aplikace použije první verzi zadané v konfiguračním souboru a je nainstalovaná.

## <a name="see-also"></a>Viz také:

[Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)
