# prova2.js

const loadScript = (url) => {
  return new Promise((resolve, reject) => {
    const script = document.createElement('script');
    script.src = url;
    script.async = true;
    script.onload = resolve;
    script.onerror = reject;
    document.head.appendChild(script);
  });
};


const fibonacci = (n, memo = {}) => {
  if (n in memo) return memo[n];
  if (n <= 1) return n;
  memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
  return memo[n];
};


const fetchData = async (url) => {
  try {
    const response = await fetch(url);
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Erro ao buscar dados:', error);
  }
};


const renderItems = (items) => {
  const container = document.getElementById('item-container');
  items.forEach((item) => {
    const element = document.createElement('div');
    element.textContent = item.name;
    container.appendChild(element);
  });
};

