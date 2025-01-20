# Time-Series Analysis for GPS Data
 This project analyzes synthetic and real-life GPS data to study periodicities using autocorrelation and periodogram functions. It simulates GPS data with daily and weekly cycles, adds noise, and evaluates algorithm performance. The project also applies these methods to the Geolife dataset to identify mobility patterns and periodic behaviors

## Task / Problem Statement  
The goal of this project is to simulate GPS data for a year with two periodic behaviors, implement custom functions to compute autocorrelation and periodograms, and test the robustness of these methods to noise in synthetic data. The real-world data from the Geolife dataset is then analyzed to identify periodic behaviors in the mobility of participants.

## Sub-Tasks  
1. **Create Synthetic Data**: Simulate GPS data with daily and weekly periodicities for 365 days.  
2. **Autocorrelation Function**: Write a function to calculate autocorrelation for the synthetic data and visualize it.  
3. **Periodogram**: Use the periodogram function to analyze the frequency domain of the synthetic data.  
4. **Noise Sensitivity**: Add noise to the data (location noise, temporal noise, etc.) and evaluate how the algorithms handle the imperfections.  
5. **Real-Life Data**: Analyze real-life GPS data from the Geolife dataset to identify mobility patterns and periodic behaviors.

## Implementation Details  
### 1. **Synthetic Data Simulation**  
   - **Trajectory Simulation**: GPS data for two periodicities—daily (8 AM to 5 PM) and weekly (weekend visits)—is generated. The data represents a person’s movement between home, work, and the supermarket.  
   - **Synthetic Data Generation**: The trajectory is simulated for 365 days with a measurement every 10 minutes, resulting in a time series of 144 (24 hours × 60 minutes ÷ 10-minute intervals) × 365 days.  
   
### 2. **Autocorrelation and Periodogram Functions**  
   - **Autocorrelation**: A custom function is written to calculate autocorrelation and detect periodicity in the synthetic data. The function identifies both daily (24 hours) and weekly (168 hours) cycles.  
   - **Periodogram**: The periodogram function is used to extract periodicities from the frequency domain. It is compared against the autocorrelation results to evaluate performance.

### 3. **Noise Handling**  
   - **Location Noise**: Gaussian noise is added to the latitude and longitude of the GPS coordinates to simulate inaccuracies in location data.  
   - **Temporal Noise**: Random shifts are introduced into the timestamps to simulate irregularities in time logging.  
   - **Performance Comparison**: Both the autocorrelation and periodogram functions are tested on noisy data to compare their sensitivity to different types and levels of noise.

### 4. **Real-Life GPS Data**  
   - The Geolife dataset is used to analyze GPS trajectories from participants over an extended period. The data is cleaned, and the methods developed in the previous parts are applied to identify periodic mobility patterns.  
   - Key insights include the identification of frequently visited locations, the temporal granularity of movement, and the periodicities present in the data.

## Metrics and Results

| Data Type    | Noise Level | Temporal Shift | Prominent Periodicity (hours) | Secondary Periodicity (hours) |
|--------------|-------------|----------------|-------------------------------|-------------------------------|
| Synthetic    | 0.1         | 15 minutes     | 168.0                         | 24.0                          |
| Synthetic    | 0.4         | 30 minutes     | 168.0                         | 24.0                          |
| Real-Life    | N/A         | N/A            | 24.0                          | 168.0                         |

### **Autocorrelation Function Results**  
- The ACF successfully detected 24-hour and 168-hour periodicities in the synthetic data, even with moderate noise levels. The method's performance degraded slightly as noise levels increased but remained reliable for detecting primary periodicities.

### **Periodogram Results**  
- The periodogram was less sensitive to temporal noise but struggled with location noise, resulting in imprecise period detection in extreme noisy conditions. However, it was able to identify the primary 168-hour periodicity even with high levels of noise.

## Conclusion  
- **ACF**: Best for detecting periodicity in the time domain, especially when the data contains minimal noise.  
- **Periodogram**: More resilient to location noise but sensitive to temporal noise. Performs well in frequency domain analysis.  
- Both methods are complementary: ACF is ideal for intuitive, time-based analysis, while the periodogram is robust for understanding frequency domain behaviors.

## Future Work  
- **Extended Noise Analysis**: Test the methods on additional types of noise, such as irregular behavior and missing data.  
- **Advanced Filtering**: Explore advanced filtering techniques to improve the accuracy of both methods under noisy conditions.  
- **Geolife Data Exploration**: Further investigate participant mobility and identify additional patterns or trends in the real-life GPS data.

## References  
- **Geolife Dataset**: [Geolife User Guide](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/User20Guide-1.2.pdf)

