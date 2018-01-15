---
title: "Požadavky na sestavení pro běžné ovládací prvky Windows Vista | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76919bcdd416ed7195e94ed1fa0b2e3f3a4d573d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Požadavky na sestavení pro běžné ovládací prvky systému Windows Vista
Knihovna Microsoft Foundation Class (MFC) podporuje běžné ovládací prvky Windows verze 6.1. Běžné ovládací prvky jsou součástí [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] a je součástí knihovny [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]. Knihovna poskytuje nové metody, které zlepšují existující třídy a nové třídy a metody, které podporují [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] běžné ovládací prvky. Když vytvoříte aplikaci, postupujte podle požadavků na kompilace a migrace, které jsou popsány v následujících částech.  
  
## <a name="compilation-requirements"></a>Požadavky na kompilace  
  
### <a name="supported-versions"></a>Podporované verze  
 Některé nové třídy a metody podporují pouze [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] a novějším, zatímco jiné metody také podporují starší operační systémy. Poznámka: v `Requirements` část každého tématu metoda určuje, kdy minimální požadovaný operační systém je [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  
  
 I když se počítač nespustí [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], můžete vytvořit aplikace knihovny MFC, který se spustí na [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] Pokud máte soubory hlaviček MFC verze 6.1 ve vašem počítači. Ale běžné ovládací prvky, které byly navrženy speciálně pro [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] fungovat pouze v daném systému a jsou ignorovány ve starších operačních systémech.  
  
### <a name="supported-character-sets"></a>Podporované znakové sady  
 Nové běžné ovládací prvky Windows podporují pouze ve znakové sadě Unicode a ne znakovou sadu ANSI. Pokud vytvoříte aplikaci na příkazovém řádku, použijte obě následující definovat (/ D) jako základní zadat Unicode – možnosti kompilátoru znaková sada:  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 Pokud vytvoříte aplikaci v sadě Visual Studio integrované vývojové prostředí (IDE), zadejte **znakové sady Unicode** možnost **znaková sada** vlastnost **obecné**  uzel vlastností projektu.  
  
 ANSI verzi několik metod MFC jsou zastaralé od verze běžné ovládací prvky Windows verze 6.1. Další informace najdete v tématu [zastaralá rozhraní API standardu ANSI](../mfc/deprecated-ansi-apis.md).  
  
## <a name="migration-requirements"></a>Požadavky na migraci  
 Pokud používáte Visual Studio IDE k vytvoření nové aplikace MFC, která používá běžné ovládací prvky Windows verze 6.1, rozhraní IDE automaticky deklaruje odpovídající manifestu. Ale pokud migrujete existující aplikaci MFC ze starší verze sady Visual Studio a chcete používat nové běžné ovládací prvky, rozhraní IDE neposkytuje automaticky manifestu informace k upgradu vaší aplikace. Místo toho je nutné ručně vložit následující zdrojový kód v souboru stdafx.h:  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [Graf hierarchie](../mfc/hierarchy-chart.md)   
 [Zastaralá rozhraní API standardu ANSI](../mfc/deprecated-ansi-apis.md)

