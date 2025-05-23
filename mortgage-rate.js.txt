export default async function handler(req, res) {
  const response = await fetch("https://api.stlouisfed.org/fred/series/observations?series_id=MORTGAGE30US&api_key=a5018b6884c847a3224f8a4bee840673&file_type=json");
  const data = await response.json();
  const latest = data.observations[data.observations.length - 1].value;

  res.status(200).json({ "30yr_fixed": parseFloat(latest) });
}
