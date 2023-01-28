using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GetUrlPaste : MonoBehaviour
{
	public static string GetRateGameId;
	public static string GetStoreId;
	public static string GetFbPageId;

	string data;
	// /////////////////////////////
	public static string YassineLink;
	public static string AppKey;
	public string urlGame; // url rate Game
	public string urlId;

	string dataId;
	string UrlStore = "your store url";

	public static GetUrlPaste _instance;
	public static GetUrlPaste instance
	{
		get { return _instance; }
	}

	[System.Obsolete]
	void Awake()
	{
		Application.targetFrameRate = 40;
		Application.runInBackground = false;
		if (_instance == null)
		{

			_instance = this;
			DontDestroyOnLoad(this);
		}
		else
		{
			Destroy(this.gameObject);
		}

		StartCoroutine(GetAppKey());

		StartCoroutine(GetUrlRateGame());
		//StartCoroutine(GetUrlFedBackGame());
		//StartCoroutine(GetStoreUrl());
		//

	}


	public void OpenRateUrl()
	{
		Application.OpenURL(GetRateGameId);
	}
	public void OpenStoreUrl()  //fedback email or url store
	{
		Application.OpenURL(UrlStore); //GetStoreId
	}
	public void OpenFbPageURL()
    {
		Application.OpenURL(GetFbPageId);
    }

	[System.Obsolete]
	IEnumerator GetUrlRateGame()
	{
		yield return new WaitForSeconds(1f);

		WWW playerlink = new WWW(urlGame);
		yield return playerlink;
		data = playerlink.text;

		GetRateGameId = getBetween(data, "RateGameUrl", "RRR");
		Debug.Log($"Url Rate {GetRateGameId}");
		//ims.AndroidAppKey = AppKey;

		yield return new WaitForSeconds(1f);

	}
	[System.Obsolete]
	IEnumerator GetUrlFedBackGame()
	{
		yield return new WaitForSeconds(1f);

		WWW playerlink = new WWW(urlGame);
		yield return playerlink;
		data = playerlink.text;

		GetFbPageId = getBetween(data, "PageFbUrl", "FB");
		Debug.Log($"Url Fb Page {GetFbPageId}");
		//ims.AndroidAppKey = AppKey;

		yield return new WaitForSeconds(1f);

	}
	[System.Obsolete]
	IEnumerator GetStoreUrl() // is true
	{
		WWW playerlink = new WWW(urlGame);
		yield return playerlink;
		data = playerlink.text;

		GetStoreId = getBetween(data, "StoreUrl", "SSS");
		Debug.Log($"Url Store {GetStoreId}");
		yield return new WaitForSeconds(1f);

	}

	// ///////////////////////////////

	public void Start()
	{

		Debug.Log("LinK :" + YassineLink);


		StartCoroutine(Wait());

	}
	void intial()
	{
		IronSource.Agent.init(AppKey);

	}

	IEnumerator Wait()
	{

		yield return new WaitForSeconds(2f);

		Debug.Log("LinK :" + YassineLink);
		//remove banner
		IronSource.Agent.loadBanner(IronSourceBannerSize.BANNER, IronSourceBannerPosition.BOTTOM);


	}
	[System.Obsolete]
	IEnumerator GetAppKey() // i need just this for call appid ironsource from server
	{
		WWW playerlink = new WWW(urlId);
		yield return playerlink;
		dataId = playerlink.text;

		AppKey = getBetween(dataId, "appkey", "xxx");
		//ims.AndroidAppKey = AppKey;
		Debug.Log($"Appkey : {AppKey}");
		yield return new WaitForSeconds(1f);
		intial();

	}

	public static string getBetween(string strSource, string strStart, string strEnd)
	{
		int Start, End;
		if (strSource.Contains(strStart) && strSource.Contains(strEnd))
		{
			Start = strSource.IndexOf(strStart, 0) + strStart.Length;
			End = strSource.IndexOf(strEnd, Start);
			return strSource.Substring(Start, End - Start);
		}
		else
		{
			return "";
		}
	}
}

