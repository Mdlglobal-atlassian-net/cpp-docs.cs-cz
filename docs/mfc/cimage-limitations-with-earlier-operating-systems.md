---
title: "Omezení služby CImage ve starších operačních systémech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CImage
dev_langs:
- C++
helpviewer_keywords:
- CImage class [MFC], limitations
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27046704975bf8f5e28f12acbfa72e860660fdbd
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2018
---
# <a name="cimage-limitations-with-earlier-operating-systems"></a>Omezení služby CImage ve starších operačních systémech
Mnoho `CImage` funkce fungovat jenom s novější verze systému Windows: Windows 95/98 nebo Windows NT 4.0 nebo Windows 2000. Tento článek popisuje verze omezení určitých metod.  
  
 [CImage::PlgBlt](../atl-mfc-shared/reference/cimage-class.md#plgblt) a [CImage::MaskBlt](../atl-mfc-shared/reference/cimage-class.md#maskblt) práce s pouze systému Windows NT 4.0 nebo novější. Nebudou správně fungovat na aplikace běžící na systému Windows 95/98 nebo novějším.  
  
 [CImage::AlphaBlend](../atl-mfc-shared/reference/cimage-class.md#alphablend) a [CImage::TransparentBlt](../atl-mfc-shared/reference/cimage-class.md#transparentblt) práce s pouze systém Windows 2000 nebo novější a Windows 98 nebo novější, protože je nutné propojit s msimg32.lib používat tyto metody. (Tato knihovna je k dispozici pouze na systémy Windows 2000 nebo novější a Windows 98 aplikace nebo novější.)  
  
 Můžete zahrnout `AlphaBlend` a `TransparentBlt` v aplikaci, která běží na systému Windows 95 nebo Windows NT 4.0, pouze v případě, že tyto metody nikdy zavolána. Pokud vaše aplikace obsahuje tyto metody, a musí běžet na starší operační systémy, musíte použít linkeru [/delayload](../build/reference/delayload-delay-load-import.md) zpoždění načítání msimg32.lib. Tak dlouho, dokud vaše aplikace nevyvolá jednu z těchto metod během spouštění v systému Windows NT 4.0 nebo systému Windows 95, nebude pokus o načtení msimg32.lib. Můžete zkontrolovat, určete, jestli průhlednost podpora je k dispozici pomocí `CImage::IsTransparencySupported` metoda.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 Kompilace aplikace, která volá tyto metody, vložit #define _WIN32_WINNT příkazu před #including všechny hlavičky systému označující, že verze systému Windows je rovna nebo větší než 5.0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 Pokud vaše aplikace není nutné spustit v operačním systému, která je starší než Windows 2000 nebo Windows 98, můžete připojit přímo k msimg32.lib bez použití **/delayload**.  
  
 [CImage::Draw](../atl-mfc-shared/reference/cimage-class.md#draw) chová odlišně, pokud se používá s Windows 2000 a Windows 98, než u systému Windows NT 4.0 nebo systému Windows 95.  
  
 Pokud je aplikace s _WIN32_WINNT nastavenou na hodnotu menší než než 0x0500, **kreslení** nebude fungovat, ale bude zpracovávat průhlednost automaticky v počítačích se systémem Windows 2000 a Windows 98 a novější.  
  
 Pokud je vaše aplikace s _WIN32_WINNT nastavena na než 0x0500 nebo vyšší, **kreslení** zpracuje průhlednost automaticky v počítačích se systémem Windows 2000 nebo Windows 98 a novější. Také bude fungovat, avšak bez podpory průhlednost s Windows NT 4.0 a systému Windows 95; ale musí používat **/delayload** zpoždění načítání msimg32. LIB, jak je popsáno výše pro `AlphaBlend` a `TransparentBlt`.  
  
## <a name="see-also"></a>Viz také  
 [CImage – třída](../atl-mfc-shared/reference/cimage-class.md)
