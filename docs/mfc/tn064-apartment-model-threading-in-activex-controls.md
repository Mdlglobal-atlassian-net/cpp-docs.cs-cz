---
title: 'TN064: Model apartment práce s vlákny v ovládacích prvcích ActiveX'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 37f8af1e4bd0fedf0b1ab14a90afdda3916c5391
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665554"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: Model apartment práce s vlákny v ovládacích prvcích ActiveX

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato technická Poznámka vysvětluje, jak povolit apartment model práce s vlákny v ovládacím prvku ActiveX. Všimněte si, že apartment model práce s vlákny je podporováno pouze ve verzi Visual C++ 4.2 nebo novější.

## <a name="what-is-apartment-model-threading"></a>Jaký je Apartment Model práce s vlákny

Model objektu apartment je přístup k podpoře vložené objekty, jako je například ovládací prvky ActiveX, v rámci aplikace s více vlákny kontejneru. I když se aplikace může mít více vláken, každá instance vloženého objektu přiřadí k jedné "apartment,", který se spustí na pouze jedno vlákno. Jinými slovy všechna volání do instance ovládacího prvku se stane ve stejném vlákně.

Různé instance stejného typu ovládacího prvku však může být přiřazen jiné objekty apartment. Ano Pokud více instancí ovládacího prvku sdílet všechna data v běžných (například statické nebo globální data), pak přístup k těmto datům sdílené se mají být chráněny objektem synchronizace, jako je kritický oddíl.

Kompletní informace o podprocesový model apartment, najdete v tématu [procesy a vlákna](/windows/desktop/ProcThread/processes-and-threads) v *OLE referenční informace pro programátory*.

## <a name="why-support-apartment-model-threading"></a>Proč podporovat Apartment Model práce s vlákny

Ovládací prvky, které podporují apartment model práce s vlákny lze použít v aplikacích s více vlákny kontejneru, které také podporu modelu objektu apartment. Pokud nepovolíte apartment model práce s vlákny, omezí potenciální sadu kontejnerů, ve kterých může váš ovládací prvek použít.

Povolení apartment model práce s vlákny je snadné pro většinu ovládací prvky, zejména v případě, že mají žádné nebo téměř žádné sdíleným datům.

## <a name="protecting-shared-data"></a>Ochrana sdílených dat

Pokud váš ovládací prvek používá sdílených dat, jako je například statické členské proměnné, přístup k, že data by měly být chráněné pomocí kritický oddíl, chcete-li zabránit ve změně data ve stejnou dobu více než jedno vlákno. Chcete-li nastavit kritický oddíl pro tento účel, deklarujte statické členské proměnné třídy `CCriticalSection` ve třídě ovládacího prvku. Použití `Lock` a `Unlock` členské funkce tento kritický oddíl objektu bez ohledu na to váš kód přistupuje ke sdíleným datům.

Zvažte například, kterou je potřeba udržovat řetězec, který je sdílena všemi instancemi třídy ovládacího prvku. Tento řetězec můžete být zachována ve statické členské proměnné a je chráněn kritický oddíl. Deklarace třídy ovládacího prvku by obsahovat následující:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

Implementace třídy by obsahovat definice pro tyto proměnné:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

Přístup k `_strShared` statický člen pak může být chráněn kritický oddíl:

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

## <a name="registering-an-apartment-model-aware-control"></a>Registrace objektu Apartment modelu – s ohledem na ovládací prvek

Ovládací prvky, které podporují apartment model práce s vlákny by měla zobrazovat tato funkce v registru tak, že přidáte hodnotu s názvem "ThreadingModel" s hodnotou "Apartment" ve své třídě ID položky registru *id třídy* \\ **InprocServer32** klíč. Chcete-li způsobit, že tento klíč k registraci pro ovládací prvek automaticky, předejte *afxRegApartmentThreading* příznak šestého parametru za účelem `AfxOleRegisterControlClass`:

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

Pokud váš projekt ovládací prvek byl vytvořen ControlWizard v jazyce Visual C++ verze 4.1 nebo novější, tento příznak již budou k dispozici ve vašem kódu. Žádné změny nejsou potřebné k registraci modelu vláken.

Pokud váš projekt byl vytvořen starší verzi ControlWizard, svůj existující kód bude mít hodnotu typu Boolean jako šestého parametru. Pokud má parametr existující hodnotu TRUE, změňte ho na *afxRegInsertable | afxRegApartmentThreading*. Pokud má parametr existující hodnotu FALSE, změňte ho na *afxRegApartmentThreading*.

Pokud váš ovládací prvek není postupujte z pravidel pro apartment model práce s vlákny, nesmí předat *afxRegApartmentThreading* v tomto parametru.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

