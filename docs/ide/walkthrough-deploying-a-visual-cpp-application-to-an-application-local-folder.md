---
title: Nasazení aplikace Visual C++ do složky App local | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: 3db193c0537869e4b99bc4c0c94cc79c70f5e827
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060660"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Návod: Nasazení aplikace Visual C++ do místní složky aplikace

Popisuje postup nasazení aplikace v jazyce Visual C++ pomocí kopírování souborů do jeho složky.

## <a name="prerequisites"></a>Požadavky

- Počítač, který nemá nainstalovanou sadu Visual Studio.

- Jiný počítač, který nemá knihoven Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>K nasazení aplikace do složky místní aplikace

1. Vytvoření a sestavení aplikace knihovny MFC podle postupu v [návod: nasazení Visual C++ Application By Using a Setup Project](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Zkopírujte příslušné soubory knihovny MFC a C Run-Time (CRT) z adresáře instalace sady Visual Studio v \\VC\\redist\\*verze* složky a pak je vložte do složky \Release\ projekt knihovny MFC. Další informace o další soubory, které možná budete muset zkopírovat najdete v tématu [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Spuštění aplikace knihovny MFC na druhém počítači, který nemá knihoven Visual C++.

   1. Zkopírujte obsah složky \Release\ a vložte je do složky aplikace na druhém počítači.

   1. Spuštění aplikace na druhém počítači.

   Spuštění aplikace je úspěšně, protože knihovny Visual C++ jsou k dispozici ve složce místní aplikace.

## <a name="see-also"></a>Viz také

[Příklady nasazení](deployment-examples.md)<br/>
