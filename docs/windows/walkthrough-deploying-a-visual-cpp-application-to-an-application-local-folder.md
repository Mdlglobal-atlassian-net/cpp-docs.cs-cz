---
title: Nasazení aplikace Visual C++ do složky místní aplikace
ms.date: 04/23/2019
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: b05dcc47aa7c0b75943f0db69797b7bf6fb55df7
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877340"
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
