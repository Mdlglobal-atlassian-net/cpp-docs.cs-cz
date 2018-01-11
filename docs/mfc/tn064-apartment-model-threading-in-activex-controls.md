---
title: "TN064: Apartment Model práce s vlákny v ovládacích prvcích ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.activex
dev_langs: C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07730d6c078dcc8fcd7ea1406f8cff6f665c9919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Model apartment práce s vlákny v ovládacích prvcích ActiveX
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato technická Poznámka vysvětluje, jak povolit apartment model práce s vlákny v ovládacím prvku ActiveX. Všimněte si, že dělení modelu objektu apartment je podporována pouze v jazyce Visual C++ verze 4.2 nebo novější.  
  
## <a name="what-is-apartment-model-threading"></a>Co je dělení modelu objektu Apartment  
 Modelu objektu apartment je přístup k podpora vložené objekty, jako je například ovládací prvky ActiveX, v rámci aplikace s více vlákny kontejneru. I když aplikace může mít více vláken, každá instance vložený objekt bude přiřazen k jedné "typu apartment,", který se spustí na pouze jedno vlákno. Jinými slovy všechna volání do instance ovládacího prvku proběhne ve stejném vlákně.  
  
 Různé instance stejného typu ovládacího prvku však může být přiřazen jiné Apartment. Ano Pokud více instancí ovládacího prvku sdílet všechna data v běžné (například statickou nebo globální data), pak přístup k těmto datům sdílené muset být chráněn na synchronizační objekt, jako je například důležitý oddíl.  
  
 Kompletní informace o model vláken typu apartment, najdete v tématu [vláken a procesů](http://msdn.microsoft.com/library/windows/desktop/ms684841) v *OLE referenční informace pro programátory*.  
  
## <a name="why-support-apartment-model-threading"></a>Proč podporují dělení modelu objektu Apartment  
 Ovládací prvky, které podporují dělení modelu objektu apartment lze použít v kontejneru vícevláknové aplikace, které také podporují modelu objektu apartment. Pokud nepovolíte dělení modelu objektu apartment, omezí potenciální sadu kontejnery, ve kterých by bylo použít vlastní ovládací prvek.  
  
 Povolení dělení modelu objektu apartment je snadné pro většinu ovládací prvky, zejména v případě, že mají žádné nebo téměř žádné sdílená data.  
  
## <a name="protecting-shared-data"></a>Ochrana sdílená Data  
 Pokud vaše řízení používá sdílená data, například statické členské proměnné, přístup k že data by měly být chráněné s kritická sekce zabránit úprava dat ve stejnou dobu více než jedno vlákno. Pro nastavení důležitý oddíl pro tento účel, deklarovat proměnnou statický člen třídy `CCriticalSection` ve třídě ovládacího prvku. Použití `Lock` a **odemčení** členské funkce této kritické části objektu bez ohledu na váš kód přistupuje k sdíleným datům.  
  
 Zvažte například řízení třídu, která je potřeba udržovat řetězec, který je sdílen všechny instance. Tento řetězec můžete udržovat statický člen proměnné a chráněn kritická sekce. Deklarace třídy ovládacího prvku by obsahovat následující:  
  
```  
class CSampleCtrl : public COleControl  
{  
 ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 Implementace pro třídu by obsahovat definice pro tyto proměnné:  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 Přístup k `_strShared` statický člen pak může být chráněn kritické části:  
  
```  
void CSampleCtrl::SomeMethod()  
{  
    _critSect.Lock();
if (_strShared.Empty())  
    _strShared = "<text>";  
    _critSect.Unlock();

 ...  
}  
```  
  
## <a name="registering-an-apartment-model-aware-control"></a>Registrace ovládacího prvku typu Apartment modelu s deklaracemi  
 Ovládací prvky, které podporují dělení modelu objektu apartment by měl být uveden tato funkce v registru přidáním pojmenované hodnotě "ThreadingModel" s hodnotou "Apartment" v jejich třída ID položky registru *id třídy* \\ **InprocServer32** klíč. Aby tento klíč automaticky zaregistrovat pro vaše ovládací prvek, předat `afxRegApartmentThreading` příznak ve šestého parametru `AfxOleRegisterControlClass`:  
  
```  
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)  
{  
    if (bRegister)  
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(), 
    m_clsid, 
    m_lpszProgID, 
    IDS_SAMPLE, 
    IDB_SAMPLE, 
    afxRegApartmentThreading, 
    _dwSampleOleMisc, 
    _tlid, 
    _wVerMajor, 
    _wVerMinor);

 else  
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}  
```  
  
 Pokud váš projekt správy vygenerovalo ControlWizard v jazyce Visual C++ verze 4.1 nebo novější, tento příznak už bude přítomná v kódu. Žádné změny jsou nezbytné pro registraci model vláken.  
  
 Pokud projekt byla vytvořena ve starší verzi ControlWizard, váš stávající kód bude mít logickou hodnotu jako šestého parametru. Pokud parametr existující hodnotu PRAVDA, změňte jej na `afxRegInsertable | afxRegApartmentThreading`. Pokud parametr existující hodnotu FALSE, změňte jej na `afxRegApartmentThreading`.  
  
 Pokud vaše řízení nedodrží pravidla pro dělení modelu objektu apartment, nesmí předat `afxRegApartmentThreading` v tomto parametru.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

