---
title: Redistribuce klientských webových aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdde0f8d4edc13e8c1e1a53d8f4393dc7c2dac40
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372467"
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací

Pokud vaše aplikace používá třídy knihovny MFC implementující ovládací prvek WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft Internet Explorer 4.0 nebo novější musí alespoň minimálně nainstalují do cílového počítače.

Instalace nejnovější verze aplikace Internet Explorer také zajišťuje, že má cílový počítač nejnovější soubory obvyklých ovládacích prvků.

Informace o instalaci minimální komponent aplikace Internet Explorer je k dispozici v následujícím článku znalostní báze Knowledge Base:

- Q185375, postupy: Vytvoření jedné EXE instalace aplikace Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))

Články znalostní báze můžete vyhledat v knihovně MSDN nebo na [ http://support.microsoft.com ](http://support.microsoft.com).

## <a name="see-also"></a>Viz také

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)