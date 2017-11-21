---
title: "Vytváření webové aplikace MFC stylu prohlížeče | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfcweb.project
dev_langs: C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c88ca61fb7dfdfbe90ed3b460c0fe9bc3a045ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Vytváření aplikací MFC ve stylu webového prohlížeče
Webové prohlížeče stylu aplikace k dispozici informace z Internetu (například HTML nebo aktivní dokumenty) nebo intranetu, jakož i složky v místním systému souborů a v síti. Odvozené třídy zobrazení aplikace z [CHtmlView](../../mfc/reference/chtmlview-class.md), efektivně provedete webový prohlížeč pro aplikaci tím, že poskytuje zobrazení pomocí ovládacího prvku WebBrowser.  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>K vytvoření aplikace webového prohlížeče, v závislosti na architektuře dokument/zobrazení MFC  
  
1.  Postupujte podle pokynů v [vytváření aplikací MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  V Průvodce aplikací MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránka, zkontrolujte některé, který **Document/view – architektura** políčka. (Můžete zvolit buď **jednotlivý dokument** nebo **více dokumentů**, ale ne **dialogové okno na základě**.)  
  
3.  Na [Přehled vytvořených tříd](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky, použijte **základní třída** rozevírací nabídky vyberte `CHtmlView`.  
  
4.  Vyberte další možnosti, které chcete součástí kostru aplikace.  
  
5.  Klikněte na tlačítko **Dokončit**.  
  
 Ovládacího prvku WebBrowser podporuje procházení webu pomocí hypertextové odkazy a navigace Uniform Resource Locator (URL). Ovládací prvek udržuje seznam historie, která umožňuje uživatelům procházet vpřed a zpět přes dříve navštívené weby, složek a dokumentů. Ovládací prvek přímo zpracuje navigační, hypertextové odkazy, seznamy historie, oblíbených položek a zabezpečení. Aplikace můžete použít ovládacího prvku WebBrowser jako kontejner pro hostování aktivního dokumentu. Proto bohatě formátovaná dokumenty, jako jsou tabulky Microsoft Excel nebo dokumentů aplikace Word lze otevřít a upravovat v rámci ovládacího prvku WebBrowser. Ovládacího prvku WebBrowser je také kontejneru ovládacího prvku ActiveX, který může hostovat ovládacího prvku ActiveX.  
  
> [!NOTE]
>  Ovládací prvek WebBrowser ActiveX (a proto `CHtmlView`) je k dispozici pouze pro aplikace spuštěné v systému Windows, ve které Internet Explorer verze 4.0 nebo novější byl nainstalován.  
  
 Protože `CHtmlView` jednoduše implementuje Microsoft ovládacího prvku webového prohlížeče, jeho podporu pro tisk není jako jiný [CView](../../mfc/reference/cview-class.md)-odvozených třídách. Místo toho ovládacího prvku WebBrowser implementuje v uživatelském rozhraní tiskárny a tisku. V důsledku toho `CHtmlView` nemá náhled tisku a rozhraní pro ostatní tisk podpory funkce neposkytuje: například [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), a [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), které jsou k dispozici v ostatních aplikacích MFC.  
  
 `CHtmlView`funguje jako obálka pro ovládací prvek webového prohlížeče, které poskytuje vaší aplikaci zobrazení webu nebo stránku HTML. Průvodce vytvoří přepsání pro [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) funkce ve třídě zobrazení, poskytne navigační odkaz na web Microsoft Visual C++:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
    NULL,
    NULL);

} 
```  
  
 Tento web můžete nahradit vlastním, nebo můžete použít [LoadFromResource –](../../mfc/reference/chtmlview-class.md#loadfromresource) – členská funkce otevřete stránku HTML, který se nachází ve skriptu prostředků projektu jako výchozí obsah pro zobrazení. Příklad:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MFCIE](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC – Průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)   
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)   
 [Stránky vlastností](../../ide/property-pages-visual-cpp.md)   
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)   
 [Nasazení aplikací](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

