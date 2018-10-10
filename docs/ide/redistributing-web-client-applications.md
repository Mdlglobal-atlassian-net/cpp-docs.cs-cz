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
ms.openlocfilehash: d036f7d46e0db84b8572b26c747947c929972517
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889929"
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací

Pokud vaše aplikace používá třídy knihovny MFC implementující ovládací prvek WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft Internet Explorer 4.0 nebo novější musí alespoň minimálně nainstalují do cílového počítače.

Instalace nejnovější verze aplikace Internet Explorer také zajišťuje, že má cílový počítač nejnovější soubory obvyklých ovládacích prvků. Další informace najdete v tématu [instalace a nasazení aplikace Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Viz také

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)