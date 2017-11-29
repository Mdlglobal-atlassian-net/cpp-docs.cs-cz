---
title: "Postupy: Aktivace a používání komponent prostředí Windows Runtime použitím knihovny WRL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bbf7c85079afe75789a7a20e04573c3d79524940
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Postupy: Aktivace a používání komponent prostředí Windows Runtime s použitím knihovny WRL
Tento dokument ukazuje, jak používat Windows Runtime C++ šablony knihovny (WRL) k inicializaci prostředí Windows Runtime a jak aktivace a používání komponent prostředí Windows Runtime.  
  
> [!NOTE]
>  Tento příklad aktivuje komponentu integrované prostředí Windows Runtime. Naučte se vytvářet vlastní komponenty, která můžete aktivovat podobným způsobem, najdete v tématu [návod: vytvoření základní komponenty prostředí Windows Runtime](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md).  
  
 Pokud chcete používat komponenty, musíte získat ukazatele rozhraní pro typ, který je implementováno modulem komponentu. A protože základní technologii prostředí Windows Runtime modelu COM (Component Object), je třeba postupovat podle pravidla COM Udržovat instance typu. Například musíte udržovat *odkazovat počet* který určuje, když je typ odstraněn z paměti.  
  
 Pro zjednodušení použití prostředí Windows Runtime, poskytuje knihovna šablon C++ prostředí Windows Runtime šabloně chytré ukazatele [ComPtr\<T >](../windows/comptr-class.md), který automaticky provede počítání odkazů. Když je deklarovat proměnnou, zadejte `ComPtr<` *název rozhraní* `>` *identifikátor*. Pro přístup rozhraní členovi, použít operátor přístup ke členu šipku (`->`) na identifikátor.  
  
> [!IMPORTANT]
>  Při volání funkce rozhraní vždy otestovat `HRESULT` vrátit hodnotu.  
  
## <a name="activating-and-using-a-windows-runtime-component"></a>Aktivace a používání komponent prostředí Windows Runtime  
 Následující postup použijte `Windows::Foundation::IUriRuntimeClass` rozhraní ukazují, jak vytvořit objekt pro vytváření aktivace pro prostředí Windows Runtime součást, vytvořit instanci této součásti a získání hodnoty vlastnosti. Také se ukazují, jak k chybě při inicializaci prostředí Windows Runtime. Úplný příklad následuje.  
  
> [!IMPORTANT]
>  I když používáte obvykle Windows knihovna šablon C++ Runtime v aplikaci pro univerzální platformu Windows, tento příklad používá konzolovou aplikaci pro obrázek. Funkce, jako `wprintf_s` nejsou k dispozici z aplikace pro univerzální platformu Windows. Další informace o typy a funkce, které můžete použít v aplikaci pro univerzální platformu Windows najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) a [aplikace Win32 a COM pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Pro aktivaci a používání komponent prostředí Windows Runtime  
  
1.  Zahrnout (`#include`) potřebné prostředí Windows Runtime, knihovna šablon C++ prostředí Windows Runtime nebo standardní knihovna C++ hlavičky.  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     Doporučujeme vám, že využíváte `using namespace` v soubor tak čitelnost kód direktivy.  
  
2.  Inicializujte vláken, ve kterém se aplikace spouští. Všechny aplikace musí inicializovat jeho přístup z více vláken a model vláken. Tento příklad používá [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) k chybě při inicializaci prostředí Windows Runtime a určuje [RO_INIT_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) jako model vláken. `RoInitializeWrapper` Třídy volání `Windows::Foundation::Initialize` při vytváření, a `Windows::Foundation::Uninitialize` kdy byla.  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     V druhém příkazu [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) vrátí operátor `HRESULT` z volání `Windows::Foundation::Initialize`.  
  
3.  Vytvoření *aktivační objekt pro vytváření* pro `ABI::Windows::Foundation::IUriRuntimeClassFactory` rozhraní.  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     Prostředí Windows Runtime používá k identifikaci typy plně kvalifikované názvy. `RuntimeClass_Windows_Foundation_Uri` Parametr je řetězec, který poskytuje prostředí Windows Runtime a obsahuje název modulu runtime požadované třídy.  
  
4.  Inicializace [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) proměnné, která představuje identifikátor URI `"http://www.microsoft.com"`.  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     V prostředí Windows Runtime není přidělit paměť pro řetězec, který bude používat prostředí Windows Runtime. Místo toho prostředí Windows Runtime vytvoří kopii vašeho řetězec do vyrovnávací paměti, že udržuje a používá pro operace a vrátí popisovač do vyrovnávací paměti vytvořený.  
  
5.  Použití `IUriRuntimeClassFactory::CreateUri` metoda factory pro vytvoření `ABI::Windows::Foundation::IUriRuntimeClass` objektu.  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  Volání `IUriRuntimeClass::get_Domain` metoda pro načtení hodnotu `Domain` vlastnost.  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  Tisk – název domény pro konzolu a vrátit. Všechny `ComPtr` a RAII objekty nechte oboru a vydávají automaticky.  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) funkce načte základní Unicode formu řetězce identifikátoru URI.  
  
 Tady je kompletní příklad:  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `wrl-consume-component.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe knihovny wrl využívat component.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)