![logo](https://github.com/feramer/feramer/assets/130202748/4e984a3a-e6d2-4e83-b940-0c5c1a17f53b)
![logo](https://github.com/feramer/feramer/assets/130202748/050cd08d-6daf-45ab-84e9-f7a370039981)

<!---
feramer/feramer is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
const init = async () => {
  const {
    bitcoin: { websocket },
  } = mempoolJS();
  
  const ws = websocket.initClient({
    options: ['blocks', 'stats', 'mempool-blocks', 'live-2h-chart'],
  });

  ws.addEventListener('message', function incoming({data}) {
    const res = JSON.parse(data.toString());
    if (res.block) {
      console.log(res.block);
    }
    if (res.mempoolInfo) {
      console.log(res.mempoolInfo);
    }
    if (res.transactions) {
      console.log(res.transactions);
    }
    if (res.mempoolBlocks) {
      console.log(res.mempoolBlocks);
    }
  });
};
init();
