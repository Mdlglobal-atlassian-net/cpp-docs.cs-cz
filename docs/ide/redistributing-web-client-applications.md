---
title: Redistribuce klientských webových aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
ms.openlocfilehash: 37ff666493ada7dada19f5731e6581603d3cb57e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512411"
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací

Pokud vaše aplikace používá třídy knihovny MFC implementující ovládací prvek WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft Internet Explorer 4.0 nebo novější musí alespoň minimálně nainstalují do cílového počítače.

Instalace nejnovější verze aplikace Internet Explorer také zajišťuje, že má cílový počítač nejnovější soubory obvyklých ovládacích prvků. Další informace najdete v tématu [instalace a nasazení aplikace Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Viz také

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)