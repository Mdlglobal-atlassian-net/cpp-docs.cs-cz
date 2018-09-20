---
title: Nasazení aplikace Visual C++ do složky App local | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b97ebffe5e44c4743df3b67987f0d27bba8a8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426273"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Návod: Nasazení aplikace Visual C++ do místní složky aplikace

Popisuje postup nasazení aplikace v jazyce Visual C++ pomocí kopírování souborů do jeho složky.

## <a name="prerequisites"></a>Požadavky

- Počítač, který nemá nainstalovanou sadu Visual Studio.

- Jiný počítač, který nemá žádné knihovny Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>K nasazení aplikace do složky místní aplikace

1. Vytvoření a sestavení aplikace knihovny MFC podle postupu v [návod: nasazení Visual C++ Application By Using a Setup Project](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Zkopírujte příslušné soubory knihovny MFC a C Run-Time (CRT) – například pro x x86 platforma a podpora kódování Unicode, kopie mfc100u.dll a msvcr100.dll ze sady Visual Studio 10.0\VC\redist\x86\—and \Program Files\Microsoft vložte je do složky \Release\ projekt knihovny MFC. Další informace o další soubory, které možná budete muset zkopírovat najdete v tématu [Determining Which DLLs to Redistribute](../ide/determining-which-dlls-to-redistribute.md).

1. Spuštění aplikace knihovny MFC na druhém počítači, který nemá žádné knihovny Visual C++.

   1.  Zkopírujte obsah složky \Release\ a vložte je do složky aplikace na druhém počítači.

   1.  Spuštění aplikace na druhém počítači.

   Spuštění aplikace je úspěšně, protože knihovny Visual C++ jsou k dispozici ve složce místní aplikace.

## <a name="see-also"></a>Viz také

[Příklady nasazení](../ide/deployment-examples.md)