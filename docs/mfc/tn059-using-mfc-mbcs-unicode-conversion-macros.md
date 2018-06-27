---
title: 'TN059: Použití převodních maker MFC MBCS Unicode | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.mbcs
dev_langs:
- C++
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e857d6f5bc2ebabb0f36a3c97e011a4f2a00d641
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953500"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Použití převodních maker MBCS/Unicode prostředí MFC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje, jak k převodu znakové sady MBCS/Unicode, které jsou definovány v AFXPRIV makra. H. Tyto makra jsou velmi užitečné, pokud vaše aplikace nabídky přímo s rozhraním OLE API nebo z nějakého důvodu, často potřebuje pro převod mezi kódování Unicode a MBCS.  
  
## <a name="overview"></a>Přehled  
 V prostředí MFC 3.x, speciální knihovny DLL se používá (MFCANS32. Knihovny DLL) automaticky převádět mezi kódování Unicode a MBCS při byly volání rozhraní OLE. Tento soubor DLL byla téměř transparentní vrstvy, který povolen OLE – aplikace má být zapsán jako kdyby OLE API a rozhraní MBCS, i když jsou vždy Unicode (s výjimkou na Macintosh). Při této vrstvy pohodlný a povolené aplikace rychle přenést z Win16 do Win32 (MFC, Microsoft Word, Microsoft Excel a VBA pro vytváření, jsou jen některé z aplikací společnosti Microsoft, které používají tuto technologii), měl někdy významně zvýšit výkon přístupů. Z tohoto důvodu MFC 4.x nepoužívá této knihovny DLL a místo toho komunikuje přímo se rozhraní OLE kódování Unicode. K tomuto účelu MFC potřebuje převést na kódování Unicode do MBCS při provádění volání rozhraní OLE a často potřeba převést na MBCS z kódování Unicode při implementaci rozhraní OLE. Chcete-li se o to postarají efektivní a snadno, počet makra byly vytvořeny v zájmu snazší tento převod.  
  
 Jedním z největších překážek, se kterými vytváření sadu makra je přidělení paměti. Protože řetězce nelze převést na místě, musíte přidělit novou paměť pro uložení převedené výsledky. To může byla provést s kódem podobný následujícímu:  
  
```  
// we want to convert an MBCS string in lpszA  
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];  
MultiByteToWideChar(CP_ACP,
    0,   
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here  
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string  
delete[] lpszW;  
```  
  
 Tento přístup jako řadu problémů. Hlavní problém je, že se jedná o velké množství kódu pro zápis, testování a ladění. Něco, co byla volání jednoduché funkce, je nyní mnohem složitější. Režie při tom je navíc významné modulu runtime. Paměť musí být přidělena v haldě a vydání pokaždé, když se provádí převod. Nakonec výše uvedený kód třeba, aby měl odpovídající `#ifdefs` přidané pro kódování Unicode a Macintosh sestavení (které nevyžadují tento převod proběhla).  
  
 Řešení, které jsme obdrželi s je vytvoření některé makra, které 1) maska rozdíl mezi různých platforem a 2) použijte příslušné schéma přidělení paměti efektivní a 3) jsou snadno vložit do existující zdrojový kód. Tady je příklad jednoho z definice:  
  
```  
#define A2W(lpa) (\  
 ((LPCSTR)lpa == NULL) NULL : (\  
    _convert = (strnlen(lpa)+1),\  
    AfxA2WHelper((LPWSTR) alloca(_convert*2),   
    lpa,
    _convert)\)\)  
```  
  
 Pomocí této makro místo výše uvedený kód a věcí jsou mnohem jednodušší:  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```  
  
 Existují další volání, kde převod je nezbytné, ale pomocí makra je jednoduchý a efektivní.  
  
 Implementace každé makro používá funkci _alloca() přidělit paměť v zásobníku místo haldě. Přidělování paměti ze zásobníku je mnohem rychlejší než přidělování v haldě paměti a velikost paměti je automaticky uvolněno při funkce je byl ukončen. Kromě toho makra Vyhněte se volání `MultiByteToWideChar` (nebo `WideCharToMultiByte`) více než jednou. K tomu je potřeba přidělování chvíli více paměti, než je nezbytné. Víme, že MBC převede do maximálně jeden **WCHAR** a že pro každou **WCHAR** jsme bude mít maximálně dva bajty MBC. Přidělování trochu více než nezbytné, ale vždy dostatečně ke zpracování převodu druhé volání druhé volání funkce Převod je předejít. Volání pomocné funkce `AfxA2Whelper` snižuje počet argument nabízených oznámení, které je třeba provést, aby bylo možné provést převod (výsledkem kódu menší, než pokud ji volat `MultiByteToWideChar` přímo).  
  
 Aby k makra tak, aby měl místa k uložení dočasné délka, je nutné deklarovat, místní proměnné s názvem _převést, který to v každé funkci, používá makra převodů. K tomu je potřeba vyvolání makro USES_CONVERSION, jak je vidět v příkladu výše.  
  
 Existují obecné Převod makra a makra konkrétní OLE. Tyto dvě různé makro sady jsou popsané dále. Všechny makra umístěny v AFXPRIV. H.  
  
## <a name="generic-conversion-macros"></a>Makra převodů obecné  
 Obecné převodních maker formuláři základní mechanismus. Příklad makro a implementace, které jsou uvedené v předchozí části, A2W, je jedna "Obecné" makro. Není ve spojení s OLE konkrétně. Sada obecné makra jsou uvedeny níže:  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 Kromě to převody text, jsou k dispozici také makra a podpůrné funkce pro převod `TEXTMETRIC`, `DEVMODE`, `BSTR`a OLE přidělené řetězce. Tyto makra jsou nad rámec této diskuse – odkazovat na AFXPRIV. H Další informace o těchto makra.  
  
## <a name="ole-conversion-macros"></a>Makra převodů OLE  
 Makra převodů OLE určené pro zpracování funkce, které očekávají **OLESTR** znaků. Pokud si projdete OLE hlavičky, uvidíte mnoho odkazů na **LPCOLESTR** a **OLECHAR**. Tyto typy se používají k odkazování na typ použitá v rozhraní OLE způsobem, který není specifické pro platformu. **OLECHAR** mapuje **char** Win16 a Macintosh platformy a **WCHAR** v Win32.  
  
 Chcete-li zachovat počet **#ifdef** direktivy v prostředí MFC kód na minimum máme podobné makro pro každý převod, kde se podílejí OLE řetězce. Nejčastěji se používají následující makra:  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 Znovu jsou podobné makra pro provádění TEXTMETRIC, DEVMODE, BSTR a OLE přidělené řetězce. Naleznete AFXPRIV. H Další informace.  
  
## <a name="other-considerations"></a>Ostatní úvahy  
 Nepoužívejte makra v úzkou smyčku. Například nechcete zápisu následující typy kódu:  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, T2COLE(lpsz));

}  
```  
  
 Výše uvedený kód může mít za následek přidělení megabajtů paměti v zásobníku v závislosti na tom, jaké obsah řetězce `lpsz` je! Také trvá, čas převést řetězec pro každé iteraci smyčky. Místo toho přesunete takové konstantní převody mimo smyčka:  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, lpszT);

}  
```  
  
 Pokud řetězec není konstantní, pak zapouzdřovat volání metody do funkce. To vám umožní převod vyrovnávací paměť na uvolnění pokaždé, když. Příklad:  
  
```  
void CallSomeMethod(int ii, LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    pI->SomeMethod(ii, T2COLE(lpsz));

}  
 
void MuchBetterIterateCode2(LPCTSTR* lpszArray)  
{  
    for (int ii = 0; ii <10000; ii++)  
    CallSomeMethod(ii, lpszArray[ii]);

}  
```  
  
 Nikdy vrátí výsledek v jedné z makra, pokud návratová hodnota znamená, že vytvoříte kopii dat před návratový. Tento kód je třeba chybná:  
  
```  
LPTSTR BadConvert(ISomeInterface* pI)  
{  
    USES_CONVERSION; 
    LPOLESTR lpsz = NULL;  
    pI->GetFileName(&lpsz);

 LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

 return lpszT; // bad! returning alloca memory  
}  
```  
  
 Výše uvedený kód může opraven změna na něco, co se zkopíruje hodnota návratovou hodnotu:  
  
```  
CString BetterConvert(ISomeInterface* pI)  
{  
    USES_CONVERSION; 
    LPOLESTR lpsz = NULL;  
    pI->GetFileName(&lpsz);

 LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

 return lpszT; // CString makes copy  
}  
```  
  
 Makra jsou snadno použitelné a snadno vkládat do kódu, ale jak zjistíte z výše uvedených upozornění, musíte být opatrní při jejich používání.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

