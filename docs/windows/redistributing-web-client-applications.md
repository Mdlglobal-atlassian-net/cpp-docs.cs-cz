---
title: Redistribuce klientských webových aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
ms.openlocfilehash: f821541efd8705e61b3292cc63713d280fd17a68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388122"
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací

Pokud vaše aplikace používá třídy knihovny MFC implementující ovládací prvek WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft Internet Explorer 4.0 nebo novější musí alespoň minimálně nainstalují do cílového počítače.

Instalace nejnovější verze aplikace Internet Explorer také zajišťuje, že má cílový počítač nejnovější soubory obvyklých ovládacích prvků. Další informace najdete v tématu [instalace a nasazení aplikace Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Viz také:

[Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)
