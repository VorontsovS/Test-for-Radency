let currentFirstLevel = 0;
let currentSecondLevel = 0;
let currentTherdLevel = 0;
let scenario1 = 0;
let count = 0;
let sum = 0;

function loadGrain(levels) {
    for (let i = 0; i < levels.length-1; i++ ){
        if (levels[i] > levels[i+1]) {
            currentFirstLevel = levels[i];
            currentSecondLevel = levels[i+1];
            scenario1 = 0;
            for (j = i+1;  j <= levels.length-2; j++){
                scenario1 = scenario1 + currentFirstLevel - levels[j];
                if (levels[j+1] >= currentFirstLevel) {
                    sum = sum + scenario1;
                    i = j;
                    j = levels.length-1;
                    currentTherdLevel = 0;
                } else {
                    if (currentSecondLevel < levels[j+1] && currentTherdLevel < levels[j+1]) {
                        currentTherdLevel = levels[j+1];
                        count = j+1;
                    };
                };
            };
            if (currentTherdLevel) {
                for (k = i+1;  k < count; k++) {
                    sum = sum + currentTherdLevel - levels[k];
                }
                i = count-1;
                currentTherdLevel = 0;
            };
        };
    };
    return sum;
};

console.log(loadGrain([2, 1, 5, 2, 7, 4, 10]));

// loadGrain([4, 1, 3]) // 2
// loadGrain([2, 1, 5, 2, 7, 4, 10]) // 7
// loadGrain([2, 0, 1, 5, 2, 7]) // 6
// loadGrain([2, 4, 2]) // 0
// loadGrain([7, 4]) // 0
// loadGrain([]) // 0