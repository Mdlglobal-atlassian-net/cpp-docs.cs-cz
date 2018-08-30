---
title: Vytvoření aplikace MFC ve stylu prohlížeče Web | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71312a1dfa70ca3fd83242f6f706654c08a4973c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217664"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Vytváření aplikací MFC ve stylu webového prohlížeče
Webovou aplikaci ve stylu prohlížeče můžete přístup k informacím z Internetu (například HTML nebo aktivní dokumenty) nebo intranet, stejně jako složky v místním systému souborů a v síti. Odvozené třídy zobrazení vaší aplikace z [CHtmlView](../../mfc/reference/chtmlview-class.md), efektivně provedete webový prohlížeč pro aplikaci tím, že poskytuje zobrazení pomocí ovládacího prvku WebBrowser.  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>K vytvoření webové aplikace v prohlížeči podle architektury dokument/zobrazení MFC  
  
1.  Postupujte podle pokynů v [vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  V Průvodce aplikací MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránce, provedení určitých, který **architekturu Document/view** je zaškrtnuté políčko. (Můžete zvolit **jednotlivý dokument** nebo **více dokumentů**, ale ne **na bázi dialogu**.)  
  
3.  Na [třídy generované v revizi](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky, použijte **základní třída** rozevírací nabídky vyberte `CHtmlView`.  
  
4.  Vyberte další možnosti, které chcete, aby integrované do kostry aplikace.  
  
5.  Klikněte na tlačítko **Dokončit**.  
  
 Ovládací prvek WebBrowser podporuje, procházení webu pomocí hypertextové odkazy a navigace Uniform Resource Locator (URL). Ovládací prvek udržuje seznam historie, který umožňuje uživateli procházet vpřed a zpět mezi předchozích navštívených stránek lokalit, složky a dokumenty. Ovládací prvek přímo zpracovává navigační, hypertextové odkazy, seznamy historie, Oblíbené položky a zabezpečení. Aplikace slouží jako kontejner pro aktivní dokument pro hostování aktivního dokumentu ovládací prvek WebBrowser. Proto bohatě formátovaná dokumenty, jako jsou tabulky Microsoft Excel nebo dokumentů aplikace Word lze otevřít a upravit v rámci ovládacího prvku WebBrowser. WebBrowser – ovládací prvek je také kontejnerem ovládacího prvku ActiveX, který může hostovat jakýkoli ovládací prvek ActiveX.  
  
> [!NOTE]
>  Ovládací prvek WebBrowser ActiveX (a tedy `CHtmlView`) je dostupná jenom pro aplikace běžící v rámci verze Windows, ve které aplikace Internet Explorer 4.0 nebo novější bylo nainstalováno.  
  
 Protože `CHtmlView` jednoduše implementuje ovládací prvek webu prohlížeče, podporu pro tisk není jako jiné [CView](../../mfc/reference/cview-class.md)-odvozené třídy. Místo toho ovládací prvek WebBrowser implementuje v uživatelském rozhraní tiskárny a tisku. V důsledku toho `CHtmlView` nemá nepodporuje náhled tisku a neposkytuje rozhraní pro další tisk funkce podpory: například [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), a [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), které jsou k dispozici v jiných aplikacích MFC.  
  
 `CHtmlView` funguje jako obálka pro ovládací prvek webového prohlížeče, která poskytuje zobrazení na webu nebo stránku HTML vaší aplikace. Průvodce vytvoří, přepíše [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) funkce ve třídě zobrazení poskytující navigační odkaz na web Microsoft Visual C++:  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Tento web můžete nahradit vlastním, nebo můžete použít [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) členské funkce a otevřete stránku HTML, který se nachází v skript prostředků projektu jako výchozí obsah pro zobrazení. Příklad:  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);
}
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC MFCIE](https://msdn.microsoft.com/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [Průvodce aplikací MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)   
 [Stránky vlastností](../../ide/property-pages-visual-cpp.md)   
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)   
 [Nasazení aplikací](https://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)

