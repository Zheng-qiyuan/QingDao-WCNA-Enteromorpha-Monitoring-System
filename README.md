# Qingdao-WCNA-Enteromorpha-Monitoring-System
Interactive GEE Web-GIS platform for monitoring Enteromorpha Prolifera in Qingdao. Features Sentinel-2 automated detection, dynamic heatmap/binary visualization, temporal NDVI inspector, and CSV/GeoTIFF export. A high-precision tool for spatiotemporal analysis of green tide outbreaks.
# Cloud-based Web-GIS Application for Spatiotemporal Monitoring of Enteromorpha Prolifera in Qingdao West Coast New Area
This is the main heading of my project, developed for the automated detection and analysis of green tides.

## Project Context (H2)
This project utilizes Google Earth Engine and Sentinel-2 satellite imagery to monitor algae outbreaks in the Yellow Sea.

### Key Objectives (H3)
- Perform high-precision spectral extraction of Enteromorpha.
- Filter out high-reflectance sediment noise in coastal waters.
- Provide interactive tools for temporal trend analysis.

---

## Lists
### Bulleted list:
- **Multi-Mode Visualization**: Switching between Binary Classification and NDVI Heatmaps.
- **Dynamic Style Manager**: Real-time color palette adjustment for better contrast.
- **Point Inspector**: On-the-fly generation of temporal NDVI charts.

### Numbered list:
1. Select a monitoring year from the dropdown menu.
2. Adjust the display mode and color theme in the control panel.
3. Click any point on the sea surface to view the NDVI trend.

---

## Text Formatting
**This is an academic project** developed at the *College of Oceanography and Space Informatics*.
~~Old manual detection methods~~ are now replaced by this **cloud-based and *automated* analysis platform**.

You can also combine **bold and _italic_**.

---

## Links and Images
[Launch GEE Monitoring Platform](https://code.earthengine.google.com/128cc7fa220b85d37a728362b2293cf2)

### 📊 System Gallery
![Main Interface](screenshot-main.png)
*Figure 1: Overview of the monitoring platform.*

![Heatmap Mode](screenshot-heatmap.png)
*Figure 2: NDVI Intensity Heatmap showing dense algae clusters.*

![Point Inspector](screenshot-chart.png)
*Figure 3: Temporal NDVI trend analysis for a selected monitoring point.*

---

## Code Blocks
Inline code: `extractAlgae(image)`

Block of code:
```javascript
function extractAlgae(img) {
    var ndvi = img.normalizedDifference(['B8', 'B4']).rename('NDVI');
    var is_not_sediment = img.select('B4').lt(1200); 
    
    return img.addBands(ndvi)
              .updateMask(water_mask)     
              .updateMask(is_not_sediment)
              .clip(study_area);
}
