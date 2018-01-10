---
title: "Nastavení aplikace, Průvodce ovládacím prvkem ActiveX knihovny MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.ctl.appset
dev_langs: C++
helpviewer_keywords: MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b63507ba50f5f9d7dfb0fe5487e2758ced02cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Nastavení aplikace, průvodce ovládacím prvkem ActiveX v prostředí MFC
Na této stránce Průvodce ovládacího prvku ActiveX knihovny MFC návrh a přidat základní funkce do nového projektu MFC ActiveX. Toto nastavení se týká vlastní aplikace a nikoli na konkrétní funkce nebo elementu ovládacího prvku.  
  
 **Běhová licence**  
 Vyberte tuto možnost k vygenerování licenční soubor uživatele k distribuci pomocí ovládacího prvku. Licence je textový soubor, *projname*.lic. Tento soubor musí být ve stejném adresáři jako instance vytvořené v prostředí návrhu ovládacího prvku knihovna DLL ovládacího prvku. Obvykle s ovládacím prvkem distribuovat tento soubor, ale vaši zákazníci Nedistribuovat.  
  
 **Generovat soubory nápovědy**  
 Vyberte tuto možnost, generovat provizorní soubory nápovědy a konfigurace projektu zahrnout Nápověda pro vaše ovládací prvek. Výchozí projekt, vytvořit, pokud není tato možnost se vygeneruje pouze **o** pole, které se zobrazí po kliknutí pravým ovládacího prvku, stisknutím klávesy F1 nebo kliknutím na **pomoci** v kontejneru ovládacího prvku.  
  
> [!NOTE]
>  Zobrazení nápovědy závisí na jak vlastního ovládacího prvku komunikuje s jeho kontejneru. Pokud zahrnete nápovědy kontejner, je nutné zajistit zpráv mezi ovládacího prvku a kontejneru správně zobrazit nápovědu.  
  
 Při generování soubory nápovědy pomocí Průvodce projektu zahrnuje následující:  
  
-   VCXPROJ soubor obsahuje kód pro sestavení a nakonfigurovat v souboru nápovědy při sestavení projektu.  
  
-   Soubor *projnamePropPage*zahrnuje souboru [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) funkce v konstruktoru.  
  
-   Soubor projname.hpj, je použít kompilátorem nápovědy k vytvoření souboru nápovědy ovládacího prvku ActiveX projektového souboru nápovědy. HPJ soubor je textový soubor obsahující informace o vytváření souboru nápovědy a cesty k další soubory (například Bitmap) obsahuje soubor nápovědy.  
  
-   Projekt obsahuje adresář HLP obsahovat rastrové soubory nápovědy projektu a soubor témat nápovědy (*projname*.rtf). Tento soubor téma nápovědy obsahuje standardní témata nápovědy pro běžné vlastnosti, události a metod podporovaných mnoho ovládacích prvků ActiveX. Můžete upravit souboru RTF, které chcete přidat nebo odebrat konkrétní témata nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

