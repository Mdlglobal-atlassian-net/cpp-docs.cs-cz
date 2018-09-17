---
title: Nastavení aplikace, Průvodce ovládacím prvkem ActiveX knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad19a4c9726378a54bd68173decd2469c17ec75
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708564"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Nastavení aplikace, průvodce ovládacím prvkem ActiveX v prostředí MFC
Na této stránce průvodce pro ovládací prvek ActiveX knihovny MFC k navrhování a přidat základní funkce do nového projektu ActiveX knihovny MFC. Tato nastavení platí pro vlastní aplikace a ne do konkrétní funkce nebo elementu ovládacího prvku.  
  
- **Licence za běhu**

   Vyberte tuto možnost, chcete-li vygenerovat soubor uživatelské licence k distribuci pomocí ovládacího prvku. Licence je textový soubor, *název_projektu*.lic. Tento soubor musí být ve stejném adresáři jako knihovnu DLL ovládacího prvku umožňující instance ovládacího prvku má být vytvořen v prostředí návrhu. Tento soubor obvykle distribuujete ovládacího prvku, ale vaši zákazníci distribuovat, není ji.  
  
- **Generovat soubory nápovědy**

   Tato možnost Generovat provizorní soubory nápovědy a nakonfigurujte projekt tak, aby obsahoval nápovědu pro ovládací prvek. Výchozí projekt vytvořit, pokud není tato možnost vygeneruje jenom **o** pole, které se zobrazí, když uživatel klikne pravým tlačítkem myši ovládací prvek, stisknutím klávesy F1 nebo kliknutím **pomáhají** v kontejneru ovládacího prvku.  
  
   > [!NOTE]
   > Zobrazení nápovědy závisí na interakci ovládacího prvku s jejím kontejnerem. Zadáte-li pomoc s kontejneru, je třeba zpracovávat zprávy mezi ovládacím prvkem a kontejneru zobrazit nápovědu odpovídajícím způsobem.  
  
   Při generování souborů nápovědy pomocí Průvodce vytvořením projektu zahrnuje následující:  
  
   - Soubor .vcxproj obsahuje kód pro vytvoření a konfigurace v souboru nápovědy při vytváření projektu.  
  
   - Soubor *projnamePropPage*obsahuje soubor .cpp [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) funkci v konstruktoru.  
  
   - Projname.hpj soubor je soubor nápovědy projekt používá kompilátor nápovědy k vytvoření souboru nápovědy ovládací prvek ActiveX. Soubor HPJ je textový soubor obsahující informace o vytváření souboru nápovědy a cesty k další soubory (například rastrové obrázky) obsahuje v souboru nápovědy.  
  
   - Projekt obsahuje adresář HLP tak, aby obsahovala rastrové soubory nápovědy projektu a souboru tématu nápovědy (*název_projektu*RTF). Tento soubor téma nápovědy obsahuje standardní témata nápovědy pro běžné vlastnosti, události a metody podporuje mnoho ovládacích prvků ActiveX. Můžete upravit soubor RTF, které chcete přidat nebo odebrat konkrétní témata nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

