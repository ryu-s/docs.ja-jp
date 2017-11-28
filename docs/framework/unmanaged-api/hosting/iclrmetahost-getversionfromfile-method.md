---
title: "ICLRMetaHost::GetVersionFromFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fcf5ca8306c4e91ff6b96bac36ad2639d81d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="10dd3-102">ICLRMetaHost::GetVersionFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="10dd3-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="10dd3-103">指定されたファイル パスから、アセンブリの元の .NET Framework コンパイル バージョン (メタデータに格納されている) を取得します。</span><span class="sxs-lookup"><span data-stu-id="10dd3-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="10dd3-104">このメソッドは、 [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="10dd3-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10dd3-105">構文</span><span class="sxs-lookup"><span data-stu-id="10dd3-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10dd3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10dd3-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="10dd3-107">[in]アセンブリの完全ファイル パス。</span><span class="sxs-lookup"><span data-stu-id="10dd3-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="10dd3-108">[out]形式で、メタデータに格納されている .NET Framework のコンパイル バージョン"v*A*.*B*[.*X*]"です。</span><span class="sxs-lookup"><span data-stu-id="10dd3-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="10dd3-109">*A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。</span><span class="sxs-lookup"><span data-stu-id="10dd3-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="10dd3-110">この文字列の長さが MAX_PATH に制限されます。</span><span class="sxs-lookup"><span data-stu-id="10dd3-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10dd3-111">この出力には、C:\Windows\Microsoft.NET\Framework 下に表示されます、.NET Framework のバージョンのディレクトリ名が一致します。</span><span class="sxs-lookup"><span data-stu-id="10dd3-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="10dd3-112">値の例は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*X*"ここで、 *X*インストールされているビルドの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="10dd3-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="10dd3-113">"V"プレフィックスが必要なことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="10dd3-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="10dd3-114">[入力、出力].サイズ`pwzbuffer`バッファー オーバーランを回避します。</span><span class="sxs-lookup"><span data-stu-id="10dd3-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10dd3-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="10dd3-115">Return Value</span></span>  
 <span data-ttu-id="10dd3-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="10dd3-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="10dd3-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10dd3-117">HRESULT</span></span>|<span data-ttu-id="10dd3-118">説明</span><span class="sxs-lookup"><span data-stu-id="10dd3-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10dd3-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="10dd3-119">S_OK</span></span>|<span data-ttu-id="10dd3-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="10dd3-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="10dd3-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="10dd3-121">E_POINTER</span></span>|<span data-ttu-id="10dd3-122">`pwzbuffer` または `pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="10dd3-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="10dd3-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="10dd3-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="10dd3-124">バッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="10dd3-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10dd3-125">要件</span><span class="sxs-lookup"><span data-stu-id="10dd3-125">Requirements</span></span>  
 <span data-ttu-id="10dd3-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="10dd3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10dd3-127">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="10dd3-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="10dd3-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="10dd3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10dd3-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10dd3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10dd3-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="10dd3-130">See Also</span></span>  
 [<span data-ttu-id="10dd3-131">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10dd3-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="10dd3-132">ホスティング</span><span class="sxs-lookup"><span data-stu-id="10dd3-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)