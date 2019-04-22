---
title: Nasazení aplikace Visual C++ do složky místní aplikace
ms.date: 09/17/2018
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: 33edf4bb736fad62928e11dd0550af6640d411ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786558"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Návod: Nasazení aplikace Visual C++ do složky místní aplikace

Popisuje postup nasazení aplikace v jazyce Visual C++ pomocí kopírování souborů do jeho složky.

## <a name="prerequisites"></a>Požadavky

- Počítač, který nemá nainstalovanou sadu Visual Studio.

- Jiný počítač, který nemá knihoven Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>K nasazení aplikace do složky místní aplikace

1. Vytvoření a sestavení aplikace knihovny MFC podle postupu v [názorný postup: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Zkopírujte příslušné soubory knihovny MFC a C Run-Time (CRT) z adresáře instalace sady Visual Studio v \\VC\\redist\\*verze* složky a pak je vložte do složky \Release\ projekt knihovny MFC. Další informace o další soubory, které možná budete muset zkopírovat najdete v tématu [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Spuštění aplikace knihovny MFC na druhém počítači, který nemá knihoven Visual C++.

   1. Zkopírujte obsah složky \Release\ a vložte je do složky aplikace na druhém počítači.

   1. Spuštění aplikace na druhém počítači.

   Spuštění aplikace je úspěšně, protože knihovny Visual C++ jsou k dispozici ve složce místní aplikace.

## <a name="see-also"></a>Viz také:

[Příklady nasazení](deployment-examples.md)<br/>
